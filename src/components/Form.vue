<template>
<div>
  <!-- form -->
  <div class="flex flex-col mx-8 my-4">
    <div class="flex flex-row mb-4">	
      <label for="ftitle" class="w-1/4">Input Title</label>
      <input type="text" v-model="title" class="border border-gray-100 p-2">
    </div>
    
    <div class="flex flex-row mb-4">
      <label for="fexc" class="w-1/4">Input Excerpt</label>
      <input type="text" v-model="exc" class="border border-gray-100 p-2">
    </div>
    
    <div class="flex flex-row mb-4">
      <label for="fimg" class="w-1/4">Input Image</label>
      <input type="text" v-model="img" class="border border-gray-100 p-2">
    </div>

    <button class="bg-blue-royal-800 justify-start text-white py-2" @click.prevent="createNew"> Submit </button>
  </div>

  <!-- bigg -->
  <div v-if="gallery.length >= 1" class="w-1/3 p-4 mx-auto flex flex-col">
		<img :src="gallery[index].img" class="w-full">
	

    <div class="bg-blue-royal-800 text-white">
      <div class="flex py-2 px-8">
        {{gallery[index].title}}
      </div>  
      <div class="flex py-2 px-8">
        {{gallery[index].exc}}
      </div>
    </div>
	</div>

  <!-- thumb -->
  <div v-if="gallery.length >= 1" class="w-3/4 mx-auto flex flex-row">
    <div v-for='(item,i) in gallery' :key='i' class="flex flex-col m-4 w-1/4 " @click='index = i'>
      <img :src="item.img" class="w-full">
      <div class="p-4 bg-blue-royal-800 text-white"> {{item.title}} </div>
    </div>
  </div>

</div>
</template>

<script>
export default {
  name:'Form',
  data: function() {
    return{
      gallery:[],
      index:0,
      title: '',
      exc: '',
      img: '',
    }
  },
  methods:{
    createNew(){
      var items = {
        'img':this.img,
        'title':this.title,
        'exc':this.exc,
      }     
      if(this.title && this.exc && this.img){
        this.gallery.push(items)
        this.img = ''
        this.title = ''
        this.exc = ''
      }else{
        alert('Ada data yang tidak di isi')
      }
    },
  }
}
</script>

<style>

</style>