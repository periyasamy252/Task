<template>
<div class="q-pa-md">
<q-layout view="lHh Lpr lff"  class="shadow-2 rounded-borders">
    <q-header elevated class="bg-blue-5 text-white" height-hint="64">
        <q-toolbar>
            <q-btn flat dense round @click="leftDrawerOpen!=leftDrawerOpen" icon="menu"/>
            <q-toolbar-title>Header</q-toolbar-title>
        </q-toolbar>
    </q-header>
    <div class='col q-ma-xl q-ml-xl justify-right' align='right'>
    <div class="row  justify-center">
      
        <q-card class='col-8'>
          <q-card-actions align='left'>
            <span class='text-light-blue=6'>Chart</span>
          </q-card-actions>
          <div id='TodoList'></div>
        </q-card>
      </div>&nbsp;
    
    <div class="row justify-center">
        <q-card class='col-8'>  
          <q-card-actions align='left'>
            <span class='text-light-blue=6'>Chart</span>
          </q-card-actions>
          <div id='AttendanceList'></div>
        </q-card>
      </div>
    </div>
    <!-- <q-drawer v-model="leftDrawerOpen" show-if-above :width="200" :breakpoint="500" bordered class="bg-blue-4"> -->
        <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="200"
        :breakpoint="500"
        bordered
        class="bg-grey-3"
      >
        <q-scroll-area class="fit">
          <q-list>

            <template v-for="(menuItem, index) in menuList" :key="index">
              <!-- <q-item clickable :active="menuItem.label == 'Menu'" v-ripple> -->
                <q-item style="margin: 0 auto" :to="menuItem.to" clickable @click="activate(menuItem)" class="GPL__drawer-item" :class="menuItem.active ? 'active' : ''">
                <q-item-section avatar>
                  <q-icon :name="menuItem.icon" />
                </q-item-section>
                <q-item-section>
                  {{menuItem.label}}
                   <!-- { { menuItem.label }} -->
                </q-item-section>
              </q-item>
              <q-separator :key="'sep' + index"  v-if="menuItem.separator" />
            </template>

          </q-list>
        </q-scroll-area>
    </q-drawer>
    <!-- <div class="row">
      <div class="col-5 q-ma-md q-mt-md q-ml-xl">
        <q-card>
          <q-card-actions align='left'>
            <span class='text-light-blue=6'>Chart</span>
          </q-card-actions>
          <div id='To-doList'></div>
        </q-card>
      </div>
    </div>  -->
     <!-- <q-page-container>
        <q-page padding>
          <p v-for="n in 15" :key="n">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugit nihil praesentium molestias a adipisci, dolore vitae odit, quidem consequatur optio voluptates asperiores pariatur eos numquam rerum delectus commodi perferendis voluptate?
          </p>
        </q-page>
      </q-page-container> -->
</q-layout>
</div>
</template>
<script>
import ApexCharts from 'apexcharts';
// import  { ref } from 'vue'
const menuList = [
   {
    icon: 'inbox',
    label: 'Profile',
    to: '/profile',
    separator: false
  },
   {
    icon: 'send',
    label: 'Menu',
    separator: false,
    to: '/menu'
  }
]
export default  {
   mounted() {
     this.generateTodoCharts()
     this.generateAttendanceCharts()

   },
  methods:{
    generateTodoCharts(){ 
    var options = {
          series: [{
          data: [400, 430, 448, 470, 540, 580, 690, 1100, 1200, 1380]
        }],
          chart: {
          type: 'bar',
          height: 350
        },
        plotOptions: {
          bar: {
            borderRadius: 4,
            horizontal: true,
          }
        },
        dataLabels: {
          enabled: false
        },
        xaxis: {
          categories: ['South Korea', 'Canada', 'United Kingdom', 'Netherlands', 'Italy', 'France', 'Japan',
            'United States', 'China', 'Germany'
          ],
        }
        };

        var chart = new ApexCharts(document.querySelector("#TodoList"), options);
        chart.render();       },

      generateAttendanceCharts(){
        var options = {
          series: [{
            name: "Desktops",
            data: [10, 41, 35, 51, 49, 62, 69, 91, 148]
        }],
          chart: {
          height: 350,
          type: 'line',
          zoom: {
            enabled: false
          }
        },
        dataLabels: {
          enabled: false
        },
        stroke: {
          curve: 'straight'
        },
        title: {
          text: 'Product Trends by Month',
          align: 'left'
        },
        grid: {
          row: {
            colors: ['#f3f3f3', 'transparent'], // takes an array which will be repeated on columns
            opacity: 0.5
          },
        },
        xaxis: {
          categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep'],
        }
        };

        var chart = new ApexCharts(document.querySelector("#AttendanceList"), options);
        chart.render();
      }

  },
//   components:  {
//     profile: require("../components/Profile.vue").default
//     },
  data ()  {
    return  {
      leftDrawerOpen: true,
      //  leftDrawerOpen: ref(false),
      menuList
    }
  }
}
</script>
