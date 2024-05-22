<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-avatar>
            <img src="https://tse3.mm.bing.net/th?id=OIP.7qkHtSkUPsVvh8JniKuPqgAAAA&pid=Api&P=0&h=180">
          </q-avatar>
          Penjualan Iphone
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/page1" label="ibox Dimas" />
      </q-tabs>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <!-- drawer content -->
      <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card">
          <q-card-section>
            {{ lorem }}
          </q-card-section>
        </q-card>

        <q-card
          class="my-card text-white"
          style="background: radial-gradient(circle, #35a2ff 0%, #014a88 100%)"
        >
          <q-card-section>
            <div class="text-h6">Our Changing Planet</div>
            <div class="text-subtitle2">by John Doe</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            {{ lorem }}
          </q-card-section>
        </q-card>

        <q-card dark bordered class="bg-grey-9 my-card">
          <q-card-section>
            <div class="text-h6">Our Changing Planet</div>
            <div class="text-subtitle2">by John Doe</div>
          </q-card-section>

          <q-separator dark inset />

          <q-card-section>
            {{ lorem }}
          </q-card-section>
        </q-card>

        <q-card flat bordered class="my-card">
          <q-card-section>
            <div class="text-h6">Our Changing Planet</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
            tempor incididunt ut labore et dolore magna aliqua.
          </q-card-section>

          <q-separator inset />

          <q-card-section>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
            tempor incididunt ut labore et dolore magna aliqua.
          </q-card-section>
        </q-card>
      </div>
    </q-drawer>

    <q-page-container>
      <div class="q-pa-md">
        <q-carousel
          animated
          v-model="slide"
          arrows
          navigation
          infinite
        >
          <q-carousel-slide :name="1" img-src="https://tse1.mm.bing.net/th?id=OIP.YeoXlvdUoTVXircy4AGSBwHaEJ&pid=Api&P=0&h=180" />
          <q-carousel-slide :name="2" img-src="https://tse3.mm.bing.net/th?id=OIP.wWQGlLLT0SztmFKNi64XsAHaFM&pid=Api&P=0&h=180" />
          <q-carousel-slide :name="3" img-src="https://tse1.mm.bing.net/th?id=OIP.Xk7mTeRos3Ujz-cb1QHgdgHaE8&pid=Api&P=0&h=180" />
          <q-carousel-slide :name="4" img-src="https://tse2.mm.bing.net/th?id=OIP.y4O4WINSNwMKEsigA7BFSQHaEK&pid=Api&P=0&h=180" />
        </q-carousel>

        <div class="q-pa-md row items-start q-gutter-md">
          <q-card v-for="(product, index) in products" :key="index" class="my-card">
            <q-img :src="product.image" :alt="product.name" class="card-img" />
            <q-card-section>
              <div class="text-h6">{{ product.name }}</div>
              <div class="text-subtitle2">{{ product.price }}</div>
            </q-card-section>
            <q-card-section class="q-pt-none">
              {{ product.description }}
            </q-card-section>
          </q-card>
        </div>
      </div>
      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://tse3.mm.bing.net/th?id=OIP.7qkHtSkUPsVvh8JniKuPqgAAAA&pid=Api&P=0&h=180">
          </q-avatar>
          <div>Ibox Dimas</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)
    const slide = ref(1)
    const products = ref([
      {
        name: 'iPhone 12',
        price: '$799',
        description: 'The latest iPhone with A14 Bionic chip.',
        image: 'https://tse2.mm.bing.net/th?id=OIP.WhrchTLCu0U8vCfoVRhhAwHaHa&pid=Api&P=0&h=180'
      },
      {
        name: 'iPhone 12 Pro',
        price: '$999',
        description: 'The latest iPhone with A14 Bionic chip and triple-camera system.',
        image: 'https://tse1.mm.bing.net/th?id=OIP.LphjdCa1QEpE1tchP1owlQHaHa&pid=Api&P=0&h=180'
      },
      {
        name: 'iPhone 12 Mini',
        price: '$699',
        description: 'Compact size with A14 Bionic chip.',
        image: 'https://tse3.mm.bing.net/th?id=OIP.lQ1ybsNSasT21OPk5LgTeAHaHa&pid=Api&P=0&h=180'
      }
    ])

    function toggleLeftDrawer () {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }

    return {
      leftDrawerOpen,
      slide,
      products,
      toggleLeftDrawer
    }
  }
}
</script>

<style>
.my-card {
  width: 300px;
}
.card-img {
  height: 200px;
  object-fit: cover;
}
</style>
