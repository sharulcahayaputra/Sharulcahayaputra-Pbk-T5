<template>
  <q-layout view="hHh lpR fFf">
    <!-- Navbar -->
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          Store Basket Sharul Gacor
        </q-toolbar-title>
        <q-btn dense flat round icon="shopping_cart" />
      </q-toolbar>
    </q-header>

    <!-- Main Content -->
    <q-page-container>
      <q-page padding class="q-pa-md">
        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          arrows
          infinite
          animated
          control-color="black"
          swipeable
          transition-prev="slide-right"
          transition-next="slide-left"
          height="550px"
          class="bg-dark text-white shadow-2 rounded-borders"
        >
          <q-carousel-slide v-for="(image, index) in carouselImages" :key="index" :name="index" :img-src="image">
          </q-carousel-slide>
        </q-carousel>

        <!-- Cards -->
        <div class="q-mt-xl row justify-center">
          <q-card v-for="(product, index) in products" :key="product.name" class="my-card q-mb-xl q-pa-md col-xs-12 col-sm-6 col-md-4 col-lg-3">
            <q-img :src="product.image" :alt="product.name" class="my-card-img">
              <q-badge color="red" floating>{{ product.discount }}Flash Sale</q-badge>
            </q-img>
            <q-card-section>
              <div class="text-h6 text-center">{{ product.name }}</div>
              <div class="text-subtitle1 text-center">{{ product.price }}</div>
            </q-card-section>
            <q-card-actions align="center">
              <q-btn flat label="Add to Cart" color="primary" />
              <q-btn flat label="Delete" color="negative" @click="deleteProduct(index)" />
            </q-card-actions>
          </q-card>
        </div>
      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-blue-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          &copy; SlamDunk
        </q-toolbar-title>
        <div>
          <q-btn flat round icon="facebook" />
          <q-btn flat round icon="twitter" />
          <q-btn flat round icon="instagram" />
        </div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const slide = ref(0);
    const carouselImages = [
      'https://i.pinimg.com/564x/c4/9b/f6/c49bf64de1863b9af245aa891559a689.jpg',  // Ganti dengan URL gambar Anda
      'https://i.pinimg.com/564x/13/fa/cf/13facf32dfc01362b3c6d1d161cd874a.jpg',
      'https://i.pinimg.com/564x/2d/fd/cc/2dfdcc63d5495b854575b7c9354cb454.jpg',
      'https://i.pinimg.com/564x/c7/83/05/c7830525961acd46904cc6d7296a68ef.jpg'
    ];
    const products = ref([
      { name: 'Manset', price: 'Rp. 100K', image: 'https://i.pinimg.com/564x/16/4a/fb/164afb87041fedffc0581331363c4cdf.jpg'},  // Ganti dengan URL gambar Anda
      { name: 'Bola Basket', price: 'Rp. 250K', image: 'https://i.pinimg.com/564x/d3/3d/20/d33d2039267e95aa858430ba4feb0ced.jpg'},
      { name: 'Kaos kaki', price: 'Rp. 50K', image: 'https://i.pinimg.com/564x/b0/ef/8a/b0ef8acaf60a1c9781046ea1b84be01e.jpg'},
      { name: 'Tas Rajut', price: 'Rp. 85K', image: 'https://i.pinimg.com/564x/13/43/34/1343346919883f18440ff84feab9850c.jpg'}
    ]);

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    };

    const deleteProduct = (index) => {
      products.value.splice(index, 1);
    };

    return {
      leftDrawerOpen,
      toggleLeftDrawer,
      slide,
      carouselImages,
      products,
      deleteProduct
    };
  }
};
</script>

<style>
.my-card {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}
.my-card-img {
  border-radius: 10px 10px 0 0;
  height: 200px;
}
.rounded-borders {
  border-radius: 10px;
}
.q-footer {
  border-top: 1px solid #003285;
}
</style>
