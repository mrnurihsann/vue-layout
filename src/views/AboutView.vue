<template>
  <div class="min-h-screen flex flex-col items-center justify-center p-6 bg-gray-100">
    <div class="d-flex justify-content-center animate__animated animate__fadeIn">
      <img :src="require('@/assets/me.png')" class="d-block pt-3" alt="" height="350px" width="350px">
    </div>
    <div class="wrapper animate__animated animate__fadeInUp">
      <p class="text-center font-medium text-lg py-3">
        Perkenalkan @nurshoes <br />
        - Brand merek ramah lingkungan dengan desain unik <br />
        dan material mewah yang bergaya dan ramah terhadap planet ini
      </p>
      <p class="text-center font-mono text-lg py-3">
        NurShoe memberikan layanan yang memperhatikan kepuasan konsumen dalam aspek kualitas material, keramahan <br />
        pelayanan, dan ketepatan estimasi waktu yang diberikan.
      </p>
      <p class="text-center font-medium text-lg py-3 animate__animated animate__fadeInUp">
        Custom your shoe with us
      </p>
      <p class="text-center font-mono text-6xl py-3 animate__animated animate__fadeInUp">
        INDONESIAN
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProfileView',
};
</script>

<style scoped>
.wrapper {
  font-family: 'Neue Machina-medium';
}
</style>
