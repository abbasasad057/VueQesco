<template>
    <v-content>
      <v-system-bar id='navbar'>
        <v-layout>
          <div class='bold'>
            ELECTRIC NETWORK GIS MAPPING
          </div>
          <v-spacer ></v-spacer>
          <div class='top'>
            ADMIN
          </div>
          <div>
            <img src="../assets/engineer.png" class="img-circle">
          </div>
        </v-layout>
      </v-system-bar>
      <widgetHolder/>
      <mapViewer>
      </mapViewer>
    </v-content>
</template>

<script>
import widgetHolder from '../components/widgetHolder';
import mapViewer from '../components/mapViewer';

export default {
  name: 'home',
  directives: {
  },
  components: {
    widgetHolder,
    mapViewer,
  },
  mounted() {
    console.log(this);
  },
}
</script>
<style>
#navbar{
  background:#0885fb;
  height:30px;
  color:#FFFFFF;
  padding: 0px
}
.bold{
  font-size: 12px;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: 800;
  padding:1em 0.5em 0.5em 1em;
}
.img-circle{
  height:1.4em;
  border-radius: 50%;
  background: #FFFFFF;
  margin:0.75em 2em 0.5em 0.5em;
}
.top{
  font-size: 12px;
  font-family: Arial, Helvetica, sans-serif;
  margin:0.65rem 0.3rem 0.3rem 0.3rem;
}
</style>
