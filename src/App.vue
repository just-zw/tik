<template>
  <div id="app">
<div class="mengceng" v-if="isshow">
  恭喜{{gamer}}获胜
<button @click="agin()" >重新开始</button>
</div>
      <template v-for="i in 9">
<HelloWorld :key="i" class="item" :show=i :iso=flat @change="change(i,flat)" ref="HWss">

</HelloWorld>
    </template>
  </div>
</template>

<script lang="ts">

import {Component,Prop,Vue,Ref}from 'vue-property-decorator'
import HelloWorld from './components/HelloWorld.vue';
@Component({
  components:{
    HelloWorld
  }
})


export default class App extends Vue{
public flat:string='o'
private num:number=0
private arr:string[]=[];
private isshow:boolean=false
private gamer:string|undefined
/* @Ref('HWss') private hw
lost(){
console.log(this.hw);

} */
agin(){
  this.isshow=false
  location.reload()
}
private change(i:number,flat:string){
  console.log(i,flat);
  this.arr[i-1]=flat
  this.num=this.num+1
if(this.num%2==0){
this.flat='o'
}else{
  this.flat='x'
};
this.isshow=this.islost(this.arr)
}
islost(localarr:string[]):boolean{
  let flat:boolean=false;
for(let i=0;i<localarr.length;i++){
  console.log(localarr[i]);
  
  if(i==0 || i==3 || i==5){
    if(localarr[i]==localarr[i+1]&&localarr[i+1]==localarr[i+2]&&localarr[i]!=undefined){
      flat=true
      this.gamer=localarr[i]
    }}
    if(i==0 || i==1 || i==2){
 if(localarr[i]==localarr[i+3]&&localarr[i+3]==localarr[i+6]&&localarr[i]!=undefined){
      flat=true
      this.gamer=localarr[i]
    }
    }
     if(i==0){
       if(localarr[i]==localarr[i+4]&&localarr[i+4]==localarr[i+8]&&localarr[i]!=undefined){
      flat=true
      this.gamer=localarr[i]
    }
     }
   if(i==2){
       if(localarr[i]==localarr[i+2]&&localarr[i+2]==localarr[i+4]&&localarr[i]!=undefined){
      flat=true
      this.gamer=localarr[i]
    }
     }   
  

}
return flat
}
}
</script>



<style scoped>
#app{
  margin-left:550px;
  margin-top: 200px;
  width: 650px;
  height: 650px;
}
.item{
  float: left;
}
.mengceng{
  position: absolute;
  
  width: 650px;
  height: 650px;
  background-color: rgba(0, 0, 0, .8);
  color: white;
  font-size: 100px;
  text-align: center;
  line-height: 650px;
}
</style>