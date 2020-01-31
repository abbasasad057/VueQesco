<template>
    <v-card id='widgetHolder' height=94px>
        <v-layout class='widgetLayout'>
          <v-content class='group'>
            <v-btn text @click="togglewarehouse" class='btn'>
              <img src="../assets/icon-warehouseconfiguration.svg" class='btn-icon'>
            </v-btn>
            <span class='span'>
              Warehouse Configuration
            </span>
          </v-content>
          <v-content class='group'>
              <v-btn text @click="toggleprint" class='btn'>
                <img src="../assets/icon-print.svg" class='btn-icon'>
              </v-btn>
              <span class='span'>
                Print
              </span>
          </v-content>
          <v-content class='group'>
              <v-btn text @click="togglebookmark" class='btn'>
                <img src="../assets/icon-bookmark.svg" class='btn-icon'>
              </v-btn>
              <span class='span'>
                Bookmark
              </span>
          </v-content>
          <v-content class='group'>
              <v-btn text @click="toggleaddfeeder" class='btn'>
                <img src="../assets/icon-add-feeder.svg" class='btn-icon'>
              </v-btn>
              <span class='span'>
                Add Feeders
              </span>
          </v-content>
          <v-content class='group'>
              <v-btn text class='btn'>
                <img src="../assets/icon-adminmodule.svg" class='btn-icon'>
              </v-btn>
              <span class='span'>
                Admin Module
              </span>
          </v-content>
          <v-content class='group'>
            <div class='in-group'>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-device.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Device</span>
              </v-btn>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-structure.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Structure</span>
              </v-btn>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-conductor.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Conductor</span>
              </v-btn>
            </div>
            <span class='span'>
                Feeder Assets Report
            </span>
          </v-content>
          <v-content class='group'>
            <div class='in-group'>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-download.svg" class="inner-icon"> </span>
                <span class="inner-cptn">GIS File</span>
              </v-btn>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-download.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Synergi File</span>
              </v-btn>
            </div>
            <span class='span'>
              Download
            </span>
          </v-content>
          <v-content class='group'>
            <div class='in-group'>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-synergeeresults.svg" class="inner-icon"> </span>
                <span class="inner-cptn">View Results</span>
              </v-btn>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-uploadsynergeeresults.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Upload Results</span>
              </v-btn>
            </div>
            <span class='span'>
              Synergi Result
            </span>
          </v-content>
          <v-content class='group'>
            <div class='in-group'>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-workorderreport.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Statuswise Logs</span>
              </v-btn>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-feederwiselogs.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Feederwise Logs</span>
              </v-btn>
            </div>
            <span class='span'>
              Work Order Report
            </span>
          </v-content>
          <v-content class='group'>
            <div class='in-group'>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-feedersurveyreport.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Feederwise</span>
              </v-btn>
              <v-btn text class='inner-btn'>
                <span><img src="../assets/icon-surveymonitorreport.svg" class="inner-icon"> </span>
                <span class="inner-cptn">Groupwise</span>
              </v-btn>
            </div>
            <span class='span'>
              Survey Report
            </span>
          </v-content>
        </v-layout>
        <warehouseConfig v-show="showWarehouse"/>
        <print v-show="showPrint"/>
        <bookmark v-show="showBookmark"/>
        <addFeeder v-show="showAddFeeder"/>
      </v-card>
</template>
<script>
import warehouseConfig from './widgets/warehouseConfig/warehouseConfig';
import print from './widgets/print/print';
import bookmark from './widgets/bookmark/bookmark';
import addFeeder from './widgets/addFeeder/addFeeder';
// import drag from '@branu-jp/v-drag'
// import {Drag} from 'vue-drag-element-directive'
// import { Draggable } from 'draggable-vue-directive';
export default {
    name: 'widgetHolder',
    // directives: {
    //         Draggable,       
    // },
    components: {
       warehouseConfig,
       print,
       bookmark,
       addFeeder
    },
    data : () => ({
    showWarehouse:false,
    showPrint:false,
    showBookmark:false,
    showAddFeeder:false
    }),
    methods:{
      togglewarehouse(){
        this.showWarehouse = !this.showWarehouse;
      },
      toggleprint(){
        this.showPrint = !this.showPrint;
      },
      togglebookmark(){
        this.showBookmark = !this.showBookmark;
      },
      toggleaddfeeder(){
        this.showAddFeeder = !this.showAddFeeder;
      }
  }
}
</script>
<style scoped>
#widgetHolder{
  z-index: 999;
}
#widgetHolder .group .btn{
  height:64px;
  padding: 4px;
  box-sizing: border-box;
  width: 100%;
}
.btn-icon{
  height: 1.6em;
  /* width: 12px; */
}
#widgetHolder .widgetLayout .group .span {
  -webkit-tap-highlight-color: rgba(0,0,0,0);
  font-style: normal;
  font-weight: 400;
  font-family: 'Muli-Regular',sans-serif;
  visibility: visible;
  cursor: default;
  box-sizing: border-box;
  padding: 0;
  border: 0;
  display: block;
  position: relative;
  left: 0;
  width: 100%;
  text-align: center;
  white-space: nowrap;
  margin: 2px 0;
  bottom: -2px;
  height: 26px;
  background-color: #ececec;
  font-size: 12px;
  color: #656565;
  line-height: 28px;
  border-top: 0;
  min-width: 133px;
}
#widgetHolder .group{
  font-style: normal;
  color: #333;
  font-weight: 400;
  font-family: 'Muli-Regular',sans-serif;
  font-size: 12px;
  visibility: visible;
  box-sizing: border-box;
  margin: 0;
  border: 0;
  padding: 0 4px 24px;
  cursor: default;
  position: relative;
  align-items: flex-start;
  align-content: flex-start;
  width: auto;
  border-left: 1px solid #d2d2d2a8;
}
#widgetHolder .widgetLayout .inner-btn{
  visibility: visible;
  box-sizing: border-box;
  touch-action: manipulation;
  font: inherit;
  color: inherit;
  overflow: visible;
  text-transform: none;
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
  cursor: pointer;
  min-width: 0;
  text-align: center;
  border: 1px solid transparent;
  outline: 0;
  position: relative;
  height: 24px;
  width: auto;
  margin: 0;
  display: inline-flex;
  flex-flow: row nowrap;
  align-items: center;
  padding: 2px 4px;
}
#widgetHolder .widgetLayout .inner-icon{
  height:12px!important;
  width: 12px!important;
}
#widgetHolder .widgetLayout .inner-cptn{
  text-transform: none;
  cursor: pointer;
  margin: 0;
  padding: 0;
  border: 0;
  display: inline-block;
  font-size: 11px;
  color: #656565;
  margin-left: 4px;
}
#widgetHolder .in-group{
  height:64px;
  font-style: normal;
  line-height: 1.42857143;
  color: #333;
  font-weight: 400;
  font-family: 'Muli-Regular',sans-serif;
  font-size: 12px;
  visibility: visible;
  cursor: default;
  box-sizing: border-box;
  padding: 0;
  border: 0;
  vertical-align: baseline;
  position: relative;
  top: calc(50% - 24px);
  max-width: 130px;
  margin: 0 auto;
}
</style>
