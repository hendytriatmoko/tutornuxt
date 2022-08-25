<template>
  <div>
    <app-bar :keranjang="cart.length" />
    <div class="mx-6">
      <v-row class="mt-3">
        <v-col cols="12" style="border:2px solid red">
          <v-row>
            <v-col cols="3"
              v-for="item in listMenu"
              :key="item.id"
            >
              <list-iklan @TambahCart="funcTambahCart" :iklan="item" />
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </div>

    <!-- dialog -->
    <v-dialog persistent width="500px" v-model="popup">
      <v-card class="pa-3">
        <div class="d-flex justify-space-between">
          <div>ini dialog</div>
          <v-icon color="red" @click="popup = false">mdi-close</v-icon>
        </div>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import ListIklan from '@/components/ListIklan.vue'
export default {
  name: 'IndexPage',
  components: {
    ListIklan: () =>
      import(/* webpackChunkName: "list-iklan" */ '@/components/ListIklan.vue'),
    AppBar: () =>
      import(/* webpackChunkName: "app-bar" */ '@/components/AppBar.vue')
  },
  data: () => ({
    listMenu:[
      {
          id:1,
          name:"martabak pandan",
          category:"Martabak",
          image:"/image/martabakpandan.jpg",
          price:25000
      },
      {
          id:2,
          name:"martabak black forest",
          category:"Martabak",
          image:"image/martabakblackforest.jpg",
          price:25000
      },
      {
          id:3,
          name:"martabak red velvet",
          category:"Martabak",
          image:"image/martabakredvelvet.jpg",
          price:25000
      },
      {
          id:4,
          name:"martabak original",
          category:"Martabak",
          image:"image/martabakoriginal.jpg",
          price:20000
      },
      {
          id:5,
          name:"martabak telor",
          category:"Martabak",
          image:"image/martabaktelor.jpg",
          price:15000
      },
      {
          id:6,
          name:"ayam bakar",
          category:"Bakar",
          image:"image/ayambakar.jpg",
          price:20000
      },
      {
          id:7,
          name:"cumi bakar",
          category:"Bakar",
          image:"/image/cumibakar.jpg",
          price:30000
      },
      {
          id:8,
          name:"ikan bakar",
          category:"Bakar",
          image:"/image/ikanbakar.jpg",
          price:15000
      },
      {
          id:9,
          name:"baby crab",
          category:"Cemilan",
          image:"/image/babycrab.jpg",
          price:10000
      },
      {
          id:10,
          name:"takoyaki",
          category:"Cemilan",
          image:"/image/takoyaki.jpg",
          price:5000
      },
      {
          id:11,
          name:"kebab",
          category:"Cemilan",
          image:"/image/kebab.jpg",
          price:15000
      },
      {
          id:12,
          name:"pisang goreng",
          category:"Goreng",
          image:"/image/pisanggoreng.jpg",
          price:1000
      },
      {
          id:13,
          name:"tahu goreng",
          category:"Goreng",
          image:"/image/tahugoreng.jpg",
          price:1000
      },
      {
          id:14,
          name:"bakwan goreng",
          category:"Goreng",
          image:"/image/bakwangoreng.jpg",
          price:1000
      },
      {
          id:15,
          name:"kentang goreng",
          category:"Goreng",
          image:"/image/kentanggoreng.jpg",
          price:5000
      },
    ],
    menuDipilih:{},
    popup:false,
    cart:[],

    // listAlamat:{
    //   nama:"Hasan",
    //   alamat:{
    //     alamat1:"cakung",
    //     alamat2:"pisangan"
    //   }
    // }
  }),
  methods: {
    pilihMenu(menu){
      this.menuDipilih = menu
      // this.popup = true
    },
    funcTambahCart: function(params){
      this.cart.push(params)
      console.log('cart', this.cart.length)
      this.$cookies.set('cart', JSON.stringify(this.cart))
    }
  },
  created(){
  }
}
</script>
