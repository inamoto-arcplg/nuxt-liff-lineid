<template>
  <section class="container">
    <p class="line-id">LINE ID：{{ lineId }}</p>
    <p><img src="https://placehold.jp/300x300.png" alt="" /></p>
  </section>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        name: '',
      },
      lineId: null,
    }
  },
  mounted() {
    if (!this.canUseLIFF()) {
      return
    }

    window.liff.init((data) => {
      this.lineId = data.context.userId || null
    })
  },
  methods: {
    canUseLIFF() {
      return navigator.userAgent.includes('Line') && window.liff
    },
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  padding: 20px;
  min-height: 100vh;
}

.line-id {
  margin-bottom: 30px;
}

.form > * {
  margin-bottom: 10px;
}
</style>
