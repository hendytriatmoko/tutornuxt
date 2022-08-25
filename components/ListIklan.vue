<template>
  <div>
    <v-card
        elevation="2"
    >
    <img @click="pilihMenu(iklan),dialog = true" style="width:100%;height:200px" :src="iklan.image" alt="gambar1">
    <div class="px-2">
        <div class="d-flex justify-space-between">
            <h3 class="mt-2">{{ iklan.name }}</h3>
            <v-icon @click="masukkanKeranjang()">mdi-cart</v-icon>
        </div>
        <p>Kategori: {{ iklan.category }}</p>
        <div class="pb-2 d-flex justify-space-between">
        <div>Harga</div>
        <div style="color:red">Rp. {{ iklan.price }}</div>
        </div>
    </div>
    </v-card>

    <!-- dialog -->
    <v-dialog v-model="dialog" width="500px">
        <v-card
            elevation="2"
            v-if="menuDipilih.id != undefined"
          >
            <img style="width:100%;height:200px" :src="menuDipilih.image" alt="gambar1">
            <div class="px-2">
              <h3 class="mt-2">{{ menuDipilih.name }}</h3>
              <p v-if="menuDipilih.category.length > 5" >Kategori: {{ menuDipilih.category.substring(0,4) }}...</p>
              <p v-else >Kategori: {{ menuDipilih.category }}</p>
              <div class="pb-2 d-flex justify-space-between">
                <div>Harga</div>
                <div style="color:red">Rp. {{ menuDipilih.price }}</div>
              </div>
            </div>
          </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
    props:['iklan'],
    data: () => ({
        dialog:false,
        menuDipilih:[],
    }),
    methods:{
        pilihMenu(item){
            this.menuDipilih = item
        },
        masukkanKeranjang(){
            // this.$cookies.set('cart', JSON.stringify(this.iklan))
            this.$emit("TambahCart", this.iklan);
        }
    },
    created(){
        // console.log('iklan',this.iklan)
    }

}
</script>

<style>

</style>