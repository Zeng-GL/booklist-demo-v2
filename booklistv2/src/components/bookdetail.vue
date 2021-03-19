<template>
<b-container>
  <b-row>
    <b-col cols="2">
      <label for="demo-sb">價格</label>
    </b-col>
    <b-col cols="5">
    <b-form-spinbutton id="price" v-model="detail.price" min="0" max="9999999999999"></b-form-spinbutton>
    </b-col>
        <b-col cols="2"><pre>{{ detail }}</pre></b-col>

  </b-row>

    <b-row>
    <b-col cols="2">
       <label for="demo-sb">數量</label>
    </b-col>
    <b-col cols="5">
    <b-form-spinbutton id="stock" v-model="detail.count" min="0" max="9999999999999"></b-form-spinbutton>
    </b-col>
    <b-col cols="2"> <b-button href="#" variant="primary">確認修改</b-button></b-col>
  </b-row>
</b-container>





  
</template>

<script>
export default {
  name: 'bookdetail',
  computed:{
    bookId(){
      return this.$route.params.bookId;
    }
  },
  data(){
    return {
        detail:{},
      
      }
  },
  
  watch:{
    bookId: async function(val){
      this.bookId = await this.fetchBookDetail(val);
    }
  },

  methods:{
    async fetchBookDetail(id){
      return await fetch("https://fe-interview-api.unnotech.com/profile/"+id)
      .then((response)=>response.json())
      .then((json)=>json);
    },
  },

  async created(){
    this.detail = await this.fetchBookDetail(this.bookId)
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
