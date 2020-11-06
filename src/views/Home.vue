<template>
  <div>
    <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100" />
    <px-assets-table v-if="!isLoading" :assets="assets" />
  </div>
</template>

<script>
import { BounceLoader } from '@saeris/vue-spinners'
import pxAssetsTable from '@/components/pxAssetsTable'
import api from '../api'

export default {
  name: 'Home',
  components: {
    pxAssetsTable,
    BounceLoader
  },

  data() {
    return {
      isLoading: false,
      assets: []
    }
  },

  created() {
    this.isLoading = true
    api
      .getAssets()
      .then(assets => (this.assets = assets))
      .finally(() => (this.isLoading = false))
  }
}
</script>

<style></style>
