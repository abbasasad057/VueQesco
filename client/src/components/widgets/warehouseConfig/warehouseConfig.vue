<template>
    <v-card class="modal-dialog" id="warehouse">
        <v-flex class="modal-header" id="warehousehead">
            Warehouse Configuration
        </v-flex>
        <v-divider/>
        <v-flex class="modal">
            <v-tabs>
                <v-tab class="modal-tab">
                    Add
                </v-tab>
                <v-tab class="modal-tab">
                    Update
                </v-tab>
                <v-tab-item>
                    <v-container class='modal-body'>
                        <div class='row'>
                            <div class="label">Warehouse Item</div>
                            <v-combobox
                                :items="warehouseitem"
                                label="Select Warehouse Item"
                                outlined
                                dense
                                class="modal-control"
                                v-model="selecteditem_add"
                            ></v-combobox>
                        </div>
                        <div class='row'>
                            <div class="label">Item Name</div>
                            <v-text-field
                                label="Item Name"
                                outlined
                                dense
                                class="modal-control"
                            ></v-text-field>
                        </div>
                        <div class='row' v-show ="selecteditem_add==='Conductor Phase'">
                            <div class="label">Conductor Type</div>
                            <v-combobox
                                :items="conductorType"
                                label="Select Condutor Type"
                                outlined
                                dense
                                class="modal-control"
                            ></v-combobox>
                        </div>
                        <div class='row' v-show ="selecteditem_add==='Conductor Phase'|| selecteditem_add==='Equipment Type'">
                            <div class="label">Prefix</div>
                            <v-text-field
                                label="Prefix"
                                outlined
                                dense
                                class="modal-control"
                            ></v-text-field>
                        </div>
                        <v-layout justify-center>
                        <v-btn class='modal-button primary'>
                            Add
                        </v-btn>
                        </v-layout>
                    </v-container>
                </v-tab-item>
                <v-tab-item>
                    <v-container class='modal-body'>
                        <div class='row'>
                            <div class="label">Warehouse Item</div>
                            <v-combobox
                                :items="warehouseitem"
                                label="Select Warehouse Item"
                                outlined
                                dense
                                class="modal-control"
                                v-model="selecteditem_up"
                            ></v-combobox>
                        </div>
                        <div class='row'>
                            <div class="label">Select Existing Item</div>
                            <v-combobox
                                label="Select Item"
                                outlined
                                dense
                                class="modal-control"
                            ></v-combobox>
                        </div>
                        <div class='row'>
                            <div class="label">Item Name</div>
                            <v-text-field
                                label="Item Name"
                                outlined
                                dense
                                class="modal-control"
                            ></v-text-field>
                        </div>
                        <div class='row' v-show ="selecteditem_up==='Conductor Phase'">
                            <div class="label">Conductor Type</div>
                            <v-combobox
                                :items="conductorType"
                                label="Select Condutor Type"
                                outlined
                                dense
                                class="modal-control"
                            ></v-combobox>
                        </div>
                        <div class='row' v-show ="selecteditem_up==='Conductor Phase'|| selecteditem_up==='Equipment Type'">
                            <div class="label">Prefix</div>
                            <v-text-field
                                label="Prefix"
                                outlined
                                dense
                                class="modal-control"
                            ></v-text-field>
                        </div>
                        <v-layout justify-center>
                            <v-btn class='modal-button primary'>
                                Update
                            </v-btn>
                        </v-layout>
                    </v-container>
                </v-tab-item>
            </v-tabs>  
        </v-flex>
    </v-card>
</template>
<script>
import {warehouseitem,conductorType} from './warehouse.json';

export default {
    name:'warehouseConfig',
    components:{
    },
    data:()=>({
        warehouseitem,
        conductorType,
        "selecteditem_add":'',
        "selecteditem_up":''
    })
}
</script>
<style>
#warehouse{
    width: 330px;
    z-index:1000 ;
    position: fixed;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-40%,-40%);
    transform: translate(-40%, -40%);
}
.label{
    display: block;
    max-width: 100%;
    margin-bottom: 5px;
    font-family: "Muli-SemiBold" sans-serif;
    font-weight: normal;
    font-size: 12px;
}
.modal-header{
    color: #0885fb;
    font-weight: bold;
    font-family: "Muli-ExtraBold",sans-serif;
    font-size: 18px;
    border-bottom: 2px solid #0885fb;
    padding: 10px 15px;
    cursor: move;
    background: #FFFF;
}
.modal{
    padding: 15px;
    min-width: 328px;
}
.modal .modal-body{
    padding: 15px ;
    margin: 0px;
    border:1px solid #adadad;
}
.modal .modal-tab{
    border:1px solid #adadad;
    border-bottom:0px;
    font-style: normal;
    font-weight: 900;
    font-size: 12px;
    font-family: "Ariel" sans-serif;
    padding: 5px 17.1px;
}

#warehouse .modal .modal-control{
    width:276px ;
    border-radius: 0%;
}
.modal .row{
    display: flex;
    flex-flow: column;
    height: 65px;
    padding: 0px 15px;
}
.modal-dialog .modal .modal-body .modal-button{
    padding: 6px 12px;
    font-weight: 400;
    text-align: center;
    cursor: pointer;
    border-radius: 3px;
    color: #fff;
    font-size: 12px;
    border-color: #adadad;
    width: 123px;
    background-color: #0768c3;
}
</style>