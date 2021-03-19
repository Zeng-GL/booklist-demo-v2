<template>
  <b-container fluid>
    <b-row>
      <b-col
        bg="3"
        md="4"
        sm="12"
        v-for="content in contents"
        :key="content.id"
      >
      <router-link :to="`/books/${content.id}`">
        <b-card
          tag="article"
          style="max-width: 20rem"
          class="mb-2"
          :Id="content.id"
          @click="showDetail"
        >
      
       <img :src="content.image">
          <b-card-text>
            {{ content.name }}
            
          </b-card-text>

         
        </b-card>
          </router-link>
      </b-col>
      
  <router-view></router-view>
  
    </b-row>
  </b-container>
</template>

<script>
// import bookdetail from './components/bookdetail.vue'
import axios from "axios";

export default {
  name: "booklist",
  //   components: {
  //     bookdetail
  //   },
  data() {
    return {
      contents: [],
      
    };
  },

  methods: {
    
    // contentChange: function () {
    //   console.log(this.contents);
    // },

    showDetail: function(){
    //   axios.get("https://fe-interview-api.unnotech.com/profile/:Id").then(
    //   (response) => {
    //     this.detail = response.data;
    //   },
    //   () => {
    //     console.log("伺服器或網路發生錯誤! 請重新整理後再試一次");
    //   }
    // )
      console.log(this.content.id)
      
      }
  },



  created: function () {
    axios.get("https://fe-interview-api.unnotech.com/books").then(
      (response) => {
        //   console.log(response.data);
        this.contents = response.data;
      },
      () => {
        console.log("伺服器或網路發生錯誤! 請重新整理後再試一次");
      }
    )},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


   
