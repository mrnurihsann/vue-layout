<template>
  <div class="profile">
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-lg-6">
                <div class="media d-flex align-items-left">
                    <img src="../assets/me.png" class="user-pic mr-3"/>
                    <div class="media-body">
                        <h5 class="mt-0 mb-1 text-start">Nur Ihsan</h5>
                        <p class="mb-0">Cras sit amet nibh libero, in gravida nulla.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>
<script>
// @ is an alias to /src
import 'bootstrap/dist/css/bootstrap.css'

export default {
  name: 'ProfileView',
  components: {

  }
}
</script>

<style scoped>
.user-pic {
    border-radius: 50%;
    height: 80px;
    width: 80px;
    margin-right: 10px; /* Menambah jarak antara gambar dan teks */
}
</style>
