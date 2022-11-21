<template >

<div>

  <div>
    
    <div class="header"> </div>
    
   
  
    <input type="checkbox" class="openSidebarMenu" id="openSidebarMenu">
    
    <label for="openSidebarMenu" class="sidebarIconToggle">MENU</label>
    <label  class="title"> SPECTACLES WOMEN </label>
    
      <div id="sidebarMenu">
    <ul class="sidebarMenuInner">
     
      <li ><a >SPECTACLES</a>
      </li>
      <li><a >SUNGLASSES</a></li>
      <li><a >HOME TRY ON</a></li>
      <li><a >PAIR FOR PAIR</a></li>
      
    </ul>
  </div>
  </div>
  
  
 
  <div>
    
   
    <b-container >
      
      <b-row   v-for="item in glasses" :key="item.id">
        <b-col    v-for="subItem in item.glass_variants" :key="subItem.id">
          <card  v-for = "(subSubItem, index) of subItem.media" :key="subSubItem.id">
            
            <img :src = "subSubItem.url" v-if = "index == 0" class="image" > 
          </card>
        </b-col>
     </b-row>
    </b-container>
  </div>

 
</div>
   

</template>

<script>




export default {
  
  
  data(){
    return {
      
      glasses:[],
      
       
     }
  },
  
  
    methods: {
      async getData() {
        const res = await fetch("http://localhost:3000/glasses");
        const finalRes = await res.json();
        this.glasses = finalRes;
      },
      
    },
 
    mounted() {
      this.getData()
    }
    
    
  
}
</script>

<style >





</style>
