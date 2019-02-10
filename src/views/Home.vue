<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>Brand List</h1>
    <div v-for="brand in brands">
      {{ brand.name }}
    </div>
  </div>
</template>



<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import axios from 'axios';


export interface Brand {
  id: number;
  name: string;
  giphyUrl: string;
}

@Component({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {
  public brands: Brand[] = [];

  private async created() {
    const response = await axios.get('/good-brands');
    this.brands = await response.data;
  }
}


