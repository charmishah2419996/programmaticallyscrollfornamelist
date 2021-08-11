<template>
  <div class="hello">
    hello vue
     <input
          type="text"
          id="inp" 
          v-model="inputTx"
          placeholder="enter text"
        />
        
     
       <div>
           <button type="button" @click="submitClick" class="btn">
              submit
          </button>
       </div>
       <div v-if="isShow">
          <h1> Entered inuput text</h1>
            {{displayTx}}
       </div>
       <div >

       </div>
       <div>
         <h1>Entered input List</h1>
         <div class="displayListcon" ref="container">
            <div v-for="(displayitem,index) in displayList" :key="index" @click="itemClick(e,displayitem)">
              <label>{{displayitem}}</label>

            </div>
          </div>
       </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  
  props: {
    msg: String
  },
  data(){
    return{
      inputTx:'',
      isShow:false,
      displayTx:'',
      displayList:[]
    }
  },

  created(){
    this.inputTx = ''
    for(var i = 0;i<50;i++){
      this.displayList.push("charmi"+i);
    }
  },
  mounted(){
    
    console.log("container", this.$refs.container.scrollHeight);
    this.$refs.container.scrollTop = this.$refs.container.scrollHeight;
  },
  updated(){
    console.log("container", this.$refs.container.scrollHeight);
    this.$refs.container.scrollTop = this.$refs.container.scrollHeight;
  },
  methods:{
   itemClick(e,item){
     console.log("event , itm",e,item)

   },
    submitClick(){
      this.displayTx = this.inputTx;
        this.isShow = true
        this.displayList.push(this.displayTx);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.displayListcon{
  height: 200px;
  overflow: scroll;
  background: red;
}
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
