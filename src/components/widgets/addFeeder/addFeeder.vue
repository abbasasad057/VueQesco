<template>
    <v-card class="modal-dialog" id="addfeeder">
        <v-flex class="modal-header" id="addfeederhead">
            Add Feeders
        </v-flex>
        <v-divider/>
        <v-flex class="modal">
            <v-radio-group v-model="codeorname" row class="radiogroup">
                    <v-radio
                        color=#0885fb
                        label="Code"
                        value="Code"
                    ></v-radio>
                    <v-spacer/>
                    <v-radio
                        color=#0885fb
                        label="Name"
                        value="Name"
                    ></v-radio>
            </v-radio-group>
            
            <div class='row'>
                <div class="label">Filter Feeders</div>
                <v-text-field
                    label="Filter Feeders"
                    outlined
                    dense
                    v-model="search"
                    class="modal-control"
                ></v-text-field>
            </div> 
            <v-tabs height="33px">
                <v-tab class="modal-tab">
                    List
                </v-tab>
                <v-tab class="modal-tab">
                    Substation
                </v-tab>
                <v-tab class="modal-tab">
                    Admin Boundary
                </v-tab>
                <v-tab-item class='modal-body' >
                    <v-container v-scroll class="checkboxelement" v-for="(flname,flid) in feederlist" :key="flid">
                            <v-checkbox
                            color="info"
                            class="shrink checkbox">
                            </v-checkbox>
                            <label class="checkboxlabel">
                                {{flname}}
                            </label>
                    </v-container>
                </v-tab-item>
                <v-tab-item class='modal-body' >
                    <v-container v-scroll class="checkboxelement">
                        <v-treeview
                        dense
                        selected-color="info"
                        selectable
                        :items="substationlist"
                        :search="search"
                        :filter="filter"
                        />
                    </v-container>
                </v-tab-item>
                <v-tab-item class='modal-body' >
                    <v-container v-scroll class="checkboxelement">
                        <v-treeview
                        dense
                        selected-color="info"
                        selectable
                        :items="adminboundarylist"
                        :search="search"
                        :filter="filter"
                        />
                    </v-container>
                </v-tab-item>
            </v-tabs>  
            <v-layout justify-center>
                <v-btn class='modal-button primary'>
                    Add
                </v-btn>
                <v-spacer/>
                <v-btn class='modal-button primary'>
                    Clear
                </v-btn>
            </v-layout>
        </v-flex>
    </v-card>
</template>
<script>
import {feederlist,feedersubstation,feederadminboundary} from './feeder.json';

export default {
    name:'addFeeder',
    components:{
    },
    data:()=>({
        feederlist,
        substationlist:[],
        adminboundarylist:[],
        codeorname:'Code',
        search:null,
        caseSensitive:false,
    }),
    methods:{
        addSubstationlist(){
            var itemid=1;
            for( var item in feedersubstation){
                for(var substation in feedersubstation[item]){
                    this.substationlist.push({id:itemid,name:substation,children:[]})
                    itemid+=1;
                    for(var feederid in feedersubstation[item][substation]){
                        this.substationlist[this.substationlist.length-1].children.push({id:itemid,name:feedersubstation[item][substation][feederid]})
                        itemid+=1;
                    }
                }
            }
        },
        addAdminBoundaryList(){
            var itemid=1;
            for( var circleitem in feederadminboundary){
                for(var circle in feederadminboundary[circleitem]){
                    this.adminboundarylist.push({id:itemid,name:circle,children:[]});
                    itemid+=1;
                    for(var circleid in feederadminboundary[circleitem][circle]){
                        itemid+=1;
                        for(var division in feederadminboundary[circleitem][circle][circleid]){
                            const adminlength=this.adminboundarylist.length-1;
                            this.adminboundarylist[adminlength].children.push({id:itemid,name:division,children:[]});
                            itemid+=1;
                            for (var substation in feederadminboundary[circleitem][circle][circleid][division]){
                                const divisionlength=this.adminboundarylist[adminlength].children.length-1;
                                this.adminboundarylist[adminlength].children[divisionlength].children.push({id:itemid,name:substation,children:[]});
                                itemid+=1;
                                for (var feederid in feederadminboundary[circleitem][circle][circleid][division][substation]){
                                    const substationlength=this.adminboundarylist[adminlength].children[divisionlength].children.length-1;
                                    const feedername=feederadminboundary[circleitem][circle][circleid][division][substation][feederid];
                                    this.adminboundarylist[adminlength].children[divisionlength].children[substationlength].children.push({id:itemid,name:feedername});
                                    itemid+=1;
                                }
                            }
                        }
                    }
                }
            }
        },
        filter () {
            return this.caseSensitive
                ? (item, search, textKey) => item[textKey].indexOf(search) > -1
                : undefined
        },
        // filter () {
        // var test='No'
        // console.log('running filter');
        // if(this.codeorname==='Code'){
        //     // test =this.caseSensitive
        //     // ? (item, search, textKey) => item[textKey].split("-")[0].indexOf(search) > -1
        //     // : undefined;
        //     test=this.caseSensitive ? (item, search, textKey) =>  item[textKey].indexOf(search)>-1
        //     :'not found';
        //     console.log(test)
        //     // return this.caseSensitive ? (item, search, textKey) =>  item[textKey]//.split("-")[0].indexOf(search) > -1
        //         //: undefined
        // }
        // else{
        //     test =this.caseSensitive
        //     ? (item, search, textKey) =>  item[textKey].split("-")[1].indexOf(search) > -1
        //     : undefined
        //     console.log(test)
        //     return this.caseSensitive
        //     ? (item, search, textKey) =>  item[textKey].split("-")[1].indexOf(search) > -1
        //     : undefined
        // }},
    },
    mounted() {
        console.log(this.codeorname);
        this.addSubstationlist();
        this.addAdminBoundaryList();
    },
}
</script>
<style scoped>
#addfeeder{
    width: 400px;
    z-index:1000 ;
    position: fixed;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-40%,-40%);
    transform: translate(-40%, -40%);
}
#addfeeder .modal-tab{
    font-size: 12px;
    font-weight:900;
    padding: 5px;
}
#addfeeder .modal .modal-control{
    border-radius: 0%;
}
#addfeeder .modal .row{
 margin-bottom: 15px;

}
#addfeeder .modal .modal-button{
    width:169px;
    height:31;
    padding:6px 15px;
    margin-top: 15px;
}
#addfeeder .modal .modal-body .checkboxelement .checkbox{
    margin-top: 0px;
}
#addfeeder .modal .modal-body .checkboxelement .checkboxlabel{
    margin:7px;
}
#addfeeder .modal .modal-body .checkboxelement{
    padding:0px;
    margin: 0px;
    font-size: 12px;
    height:20px;
    display: inline-flex;
}
#addfeeder .modal .radiogroup{
    margin-top: 0px;
}
#addfeeder .modal .modal-body{
    overflow:auto;
    height: 167px;
    padding: 10px;
    margin: 0px;
}
</style>