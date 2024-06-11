<template>
  <div class="home min-h-screen flex flex-col items-center justify-center p-6 bg-gray-100">
    <div class="max-w-6xl w-full flex flex-col items-center bg-white text-black transition duration-500">
      <h1 class="text-5xl font-bold mb-4 animate__animated animate__fadeInDown">Welcome to Nur Shoe Store</h1>
      <p class="text-lg text-gray-700 mb-6 text-center animate__animated animate__fadeInUp">
        Discover our exclusive collection of shoes.
      </p>
      <div class="flex flex-wrap justify-center mb-6 animate__animated animate__zoomIn">
        <div v-for="(shoe, index) in shoes" :key="index" class="bg-white rounded-lg shadow-lg p-4 flex-none w-60 flex flex-col items-center text-center mb-4 mr-4">
          <img :src="shoe.images.front" alt="Front View" class="h-32 rounded shadow-lg mb-4 animate__animated animate__zoomIn" style="width: 200px; margin-top: 15px;">
          <img :src="shoe.images.side" alt="Side View" class="h-32 rounded shadow-lg mb-4 animate__animated animate__zoomIn" style="width: 200px; margin-top: 15px;">
          <img :src="shoe.images.back" alt="Back View" class="h-32 rounded shadow-lg mb-4 animate__animated animate__zoomIn" style="width: 200px; margin-top: 15px;">
          <h2 class="text-xl font-semibold text-gray-900">{{ shoe.name }}</h2>
          <p class="text-gray-700 mt-2">{{ shoe.description }}</p>
          <p class="text-gray-900 font-bold mt-2">{{ shoe.price }}</p>
          <button @click="showDetails(shoe)" class="mt-4 px-4 py-2 bg-blue-500 text-dark rounded">Detail</button>
          <a :href="generateWhatsappLink(shoe)" target="_blank" class="mt-2 px-4 py-2 bg-green-500 text-dark rounded inline-flex items-center">
            <i class="fab fa-whatsapp mr-2"></i> Hubungi via WhatsApp
          </a>
          <a :href="generateWhatsappLink(shoe)" target="_blank" class="mt-2 px-4 py-2 bg-yellow-500 text-white rounded">Beli</a>
        </div>
      </div>
    </div>

    <!-- Modal untuk detail gambar -->
    <div v-if="selectedShoe" class="fixed inset-0 bg-gray-800 bg-opacity-75 flex items-center justify-center">
      <div class="bg-white rounded-lg p-6 max-w-md mx-auto">
        <img :src="selectedShoe.images.front" alt="Front View" class="rounded shadow-lg mb-4">
        <h2 class="text-2xl font-semibold text-dark-900">{{ selectedShoe.name }}</h2>
        <p class="text-dark-700 mt-2">{{ selectedShoe.description }}</p>
        <p class="text-dark-900 font-bold mt-2">{{ selectedShoe.price }}</p>
        <a :href="whatsappLink" target="_blank" class="mt-4 px-4 py-2 bg-green-500 text-dark rounded inline-flex items-center">
          <i class="fab fa-whatsapp mr-2"></i> Hubungi via WhatsApp
        </a>
        <button @click="selectedShoe = null" class="mt-4 px-4 py-2 bg-red-500 text-dark rounded">Tutup</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      shoes: [
        { 
          name: 'Running Shoe', 
          description: 'Comfortable and lightweight running shoe.', 
          price: '$100', 
          images: {
            front: 'https://i.pinimg.com/564x/5c/28/14/5c2814df14dc015a9d6664c13fc27514.jpg',
            side: 'https://i.pinimg.com/736x/be/72/99/be7299232355480cf87b4693d2ae3bae.jpg',
            back: 'https://i.pinimg.com/564x/88/8a/25/888a2512bfc39102ce9e01435883bacc.jpg'
          }
        },
        { 
          name: 'Basketball Shoe', 
          description: 'High-top basketball shoe for maximum support.', 
          price: '$120', 
          images: {
            front: 'https://i.pinimg.com/564x/f8/6a/ff/f86aff8ed64c6a36b3e4230500d1df57.jpg',
            side: 'https://i.pinimg.com/564x/49/4a/4f/494a4fca2c24aeb55f0ade614f040950.jpg',
            back: 'https://i.pinimg.com/564x/6c/d2/34/6cd23423d98238c90b9948219f62608f.jpg'
          }
        },
        { 
          name: 'Soccer Cleat', 
          description: 'Durable cleats for soccer players.', 
          price: '$90', 
          images: {
            front: 'https://i.pinimg.com/564x/7c/4b/67/7c4b679dfddc16475c53f314de69b4a8.jpg',
            side: 'https://i.pinimg.com/564x/39/29/ad/3929ad194020a9b48e691190db60c2e7.jpg',
            back: 'https://i.pinimg.com/564x/8e/23/b7/8e23b7de399e9256eeb36399baf4b583.jpg' 
          }
        },
        { 
          name: 'Casual Sneaker', 
          description: 'Stylish and comfortable casual wear.', 
          price: '$80', 
          images: { 
            front: 'https://i.pinimg.com/564x/31/76/93/31769326950dc226e891d2ce0dfa3b5e.jpg',
            side: 'https://i.pinimg.com/564x/3c/9b/08/3c9b08e2d5683122b7a9e47d64c9130f.jpg',
            back: 'https://i.pinimg.com/564x/d6/ce/c3/d6cec3747622fac3bb8d1d7c7430511d.jpg'
          }
        },
        { 
          name: 'Formal Shoe', 
          description: 'Elegant formal shoes for special occasions.', 
          price: '$150', 
          images: {
            front: 'https://i.pinimg.com/564x/5a/80/57/5a805794b18d4367664f40abcce4f41b.jpg',
            side: 'https://i.pinimg.com/564x/60/80/bd/6080bdd15b4e7327deb6360819aca5ac.jpg',
            back: 'https://i.pinimg.com/564x/a5/f3/b1/a5f3b10d5756e856ad7d9dd935db4383.jpg'
          } 
        },
        { 
          name: 'Hiking Boot', 
          description: 'Rugged boots for outdoor adventures.', 
          price: '$130', 
          images: {
            front: 'https://i.pinimg.com/564x/da/a3/dc/daa3dc8c50ab8542af89395be590754f.jpg',
            side: 'https://i.pinimg.com/564x/96/23/68/96236880a44f277b48ccdee6ac7c27ea.jpg',
            back: 'https://i.pinimg.com/564x/b9/97/aa/b997aa00b7ccf71429d2de92d016b4ab.jpg'
          } 
        },
        { 
          name: 'Tennis Shoe', 
          description: 'Lightweight and durable tennis shoes.', 
          price: '$95', 
          images: {
            front: 'https://i.pinimg.com/564x/a5/90/7a/a5907a6dcad099619d405dcc23a24674.jpg',
            side: 'https://i.pinimg.com/736x/05/ef/9f/05ef9fa0ad49f41c95811b1788ff995e.jpg',
            back: 'https://i.pinimg.com/564x/05/0e/d1/050ed17b9eb72dd376e1ca48ef767b91.jpg'
          } 
        },
        { 
          name: 'Slip-On', 
          description: 'Convenient slip-on shoes for everyday use.', 
          price: '$70', 
          images: {
            front: 'https://i.pinimg.com/564x/f8/0e/36/f80e36edc3649cb13947c7e799f963e2.jpg',
            side: 'https://i.pinimg.com/736x/74/20/c0/7420c0f6894a0f78d94de6866eff56ee.jpg',
            back: 'https://i.pinimg.com/736x/20/ad/01/20ad0100af13e21317d72972cd47d371.jpg'
          } 
         },
        { 
          name: 'Sandals', 
          description: 'Comfortable sandals for casual wear.', 
          price: '$60', 
          images: {
            front: 'https://i.pinimg.com/736x/c9/90/3b/c9903b54d32a04408fc602fabf3982a7.jpg',
            side: 'https://i.pinimg.com/564x/73/1b/54/731b54db47372107f8411b82fd85df8e.jpg',
            back: 'https://i.pinimg.com/736x/c5/dd/e9/c5dde9ab62b8a388057d2ef304af2834.jpg'
          } 
         },
        { 
          name: 'Boots', 
          description: 'Warm and stylish boots for winter.', 
          price: '$140', 
          images: {
            front: 'https://i.pinimg.com/564x/97/c2/c4/97c2c4d1035d52eacf565ba3e27275e0.jpg',
            side: 'https://i.pinimg.com/564x/b2/a4/61/b2a46187bb6ad2c13bea71c40c5c06ce.jpg',
            back: 'https://i.pinimg.com/736x/96/c5/d5/96c5d58a6f8eff866215d9687e6fe80e.jpg'
          } 
         },
      ],
      selectedShoe: null,
    };
  },
  computed: {
    whatsappLink() {
      return `https://wa.me/6289652171686?text=Halo%20Admin,%20Saya%20tertarik%20dengan%20produk%20${this.selectedShoe.name}`;
    },
  },
  methods: {
    showDetails(shoe) {
      this.selectedShoe = shoe;
    },
    generateWhatsappLink(shoe) {
      return `https://wa.me/6289652171686?text=Halo%20Admin,%20Saya%20tertarik%20dengan%20produk%20${shoe.name}`;
    },
  },
};
</script>
 
<style>
@import 'https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css';
@import 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css';
</style>
