<template>
  <div>
    keranjang
  </div>
</template>

<script>
export default {
    data: () => ({
      keranjang:[]
    }),
    methods: {
    },
    created(){
      this.keranjang = this.$cookies.get('cart')
      console.log('keranjang', this.keranjang)
    }
}
</script>

<style>

</style>