<template>
  <div>
      <v-toolbar class="px-2">
        <h3 >Makanan</h3>
        <v-spacer></v-spacer>
        <v-badge :content="keranjang > 0 ? keranjang : '0'"><v-icon @click="toKeranjang()">mdi-cart</v-icon></v-badge>
      </v-toolbar>
    <br>
  </div>
</template>

<script>
export default {
    props:['keranjang'],
    data: () => ({
    }),
    methods: {
        toKeranjang(){
            this.$router.push('/cart/keranjang')
            // console.log('ok')
        }
    },
    created(){
    }

}
</script>

<style>

</style>