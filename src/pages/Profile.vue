<template>
<div class="q-pa-md">
<q-layout view="lHh Lpr lff"  class="shadow-2 rounded-borders">
    <q-header elevated class="bg-blue-5 text-white" height-hint="64">
        <q-toolbar>
            <q-btn flat dense round @click="leftDrawerOpen!=leftDrawerOpen" icon="menu"/>
            <q-toolbar-title>Profile</q-toolbar-title>
        </q-toolbar>
    </q-header>
<div class="fixed-center text-h6">Edit Profile</div>
<q-card class="fixed-center" style="width:400px;height:600px; background-color: #f0f5f5;">
    <div class="q-ml-lg text-h6">Profile</div>
    <q-card-section>
        <div class="row q-ma-md" align="center">
            <div class="profile-img col-md-4 col-sm-12 col-sm-12 col-xs-12 q-mt-md"
            align="center">
            <q-avatar rounded size="130px">
                <img :src="img" />
            </q-avatar>
        </div></div>
        <div class="row" align="center">
            <div class="col">
                <q-input label="Name" v-model="name"></q-input>
            </div></div>
            <div class="row" align="center">
                <div class="col">
                <q-input label="Email" v-model="email"></q-input>
            </div></div>
            <div class="row" align="center">
            <div class="col">
                <q-input label="Phone" v-model="phone"></q-input>
            </div></div>
            <div class="row" align="center">
            <div class="col">
                <q-input label="Address" v-model="address"></q-input>
            </div></div>
            <div class="row" align="center">
            <div class="col">
                <q-input label="Pincode" v-model="pincode"></q-input>
            </div></div>
            <q-card-actions>
            <div class="col-6" align="right">
                <q-btn label="Save" color="green-4"></q-btn>
              </div>
            </q-card-actions>
    </q-card-section>
</q-card>
</q-layout>
</div>
</template>
<script>
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
  data ()  {
    return  {
        leftDrawerOpen: true,
      //  leftDrawerOpen: ref(false),
      menuList,
      img: '',
      name: '',
      email: '',
      phone: '',
      address: '',
      pincode: ''
    }
  }
}
</script>
