<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
          aria-label="Menu"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
         <div class="text-h3">Todo</div>
         <div class="text-subtitle">{{todaysDate}}</div>
      </div>
        <q-img src="statics/Tulips.jpg " class="header-image absolute-top" />
    </q-header>

      <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 138px); margin-top: 138px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item clickable v-ripple to="/">
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                Todo
              </q-item-section>
            </q-item>
             <q-item clickable v-ripple to="/Help">
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png" style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="statics/Tulips.jpg" style="height:138px">
            </q-avatar>
            <div class="text-weight-bold">Maryum Sheikh</div>
            <div>@maryum sheikh</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
     
      <keep-alive>
         <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar'
export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: false
    }
  }
  ,
  computed:{
    todaysDate(){
      let timeStamp = Date.now()
      return date.formatDate(timeStamp, 'dddd  D MMMM')
    }
   
  }
 }
</script>

<style lang="scss">
.header-image {
  height:100%;
  z-index:-1;
  opacity:0.2;
}
</style>
