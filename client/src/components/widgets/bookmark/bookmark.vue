<template>
    <v-card class="modal-dialog" id="bookmark">
        <v-flex class="modal-header" id="bookmarkhead">
            Bookmark
        </v-flex>
        <v-divider/>
        <v-flex class="modal">
            <v-layout>
                <div class='row'>
                        <v-text-field
                            label="Add Bookmark"
                            outlined
                            dense
                            class="modal-control"
                            v-model="bookmarkname"
                        ></v-text-field>
                </div>
                <v-spacer/>
                <v-btn class='modal-button primary' @click="addBookmark">
                    Add
                </v-btn>
            </v-layout>
            <v-container class='modal-body' id='bookmark-body'>
                <v-content v-for="(bookmark,index) in bookmarklist" :key=bookmark.name>
                    <v-layout class='bookmark-item'>
                        <label class="bookmark-label" @click="zoomToBookmark(index)">
                            {{bookmark.name}}
                        </label>
                        <v-spacer/>
                        <i class="fa fa-trash-o bookmark-icon" @click="$delete(bookmarklist,index)"/>
                    </v-layout>
                    <v-divider/>
                </v-content>
            </v-container>  
        </v-flex>
    </v-card>
</template>
<script>
export default {
    name:'bookmark',
    components:{
    },
    data:()=>({
        bookmarkname:'',
        bookmarklist:[],
    }),
    methods:{
        addBookmark(){
            if(this.bookmarkname){
                this.bookmarklist.push({
                    name:this.bookmarkname,
                    extent:this.$store.state.map.getBounds(),
                })
            }
        },
        zoomToBookmark(index){
            var extent=this.bookmarklist[index].extent
            if(extent){
            this.$store.state.map.fitBounds(extent)
            }
        }
    }
}
</script>
<style>
#bookmark{
    width: 400px;
    z-index:1000 ;
    position: fixed;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-40%,-40%);
    transform: translate(-40%, -40%);
}
#bookmark .modal .modal-button{
    padding: 6px 12px;
    font-weight: 400;
    text-align: center;
    cursor: pointer;
    border-radius: 3px;
    color: #fff;
    font-size: 12px;
    border-color: #adadad;
    width: 123px;
}
#bookmark .modal .modal-control{
    border-radius: 0%;
}
#bookmark .modal .modal-body{
    height:200px;
    padding: 10px 5px;
}
#bookmark #bookmark-body .bookmark-item{
    padding:0px 15px;
    font-size: 12px;
    font-weight: 400;
    margin: 5px 0px;
}
#bookmark #bookmark-body .bookmark-label:hover {
    cursor: pointer;
    color: #0885fb;
}
#bookmark #bookmark-body .bookmark-icon{
    font-size:14px
}
#bookmark #bookmark-body .bookmark-icon:hover {
    cursor: pointer;
    color: #0885fb;

}
</style>