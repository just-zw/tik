<template>
  <div id="Hw">
    <div class="one" :class="[classstyle,myiso,myisos]" @click="change()" @mouseenter="enter()" @mouseleave="leave()"></div>
  </div>
</template>

<script lang="ts">
  import { Component, Prop, Vue, Watch,Emit } from 'vue-property-decorator'
@Component({})
export default class HelloWorld extends Vue{
  private flats:number=0
  private classstyle:string|undefined
  private myiso:string|undefined=""
  private myisos:string|undefined=''
@Prop(Number) private show:number|undefined
@Prop(String) private iso:string|undefined
created(){
  if(this.show==1 || this.show==2 || this.show==4|| this.show==5){
this.classstyle="bottom right"
  }
  else if(this.show==3|| this.show==6){
    this.classstyle="bottom"
  }
  else if(this.show==7|| this.show==8){
this.classstyle="right"
  }else{
   this.classstyle='' 
  };
/*   this.myiso=this.iso */
/*   this.iso='' */
};
@Emit()
change(){
this.flats++
};
@Watch('iso')
changiso(newvalue:string,oldvalue:string){  
if(this.flats!=0){ 
   if(this.myisos==""){
  this.myisos=oldvalue+'s'
}
this.myiso=newvalue
}
} 
private enter(){
if(this.myisos==""){
   this.myiso=this.iso
}

}
private leave(){
if(this.myisos==""){ 
   this.myiso=""}
  
}
}
  
</script>

<style scoped>
.one{
  width: 200px;
  height: 200px;
}
.left{
  border-left: 10px solid black;
}
.right{
  border-right: 10px solid black;
}
.top{
  border-top: 10px solid black;
}
.bottom{
  border-bottom: 10px solid black;
}
.o{

}
.o::after{
  content: 'o';
  font-size: 150px;
  margin-left: 55px;
  color: cadetblue;
}
.x{

}
.x::after{
  content: 'x';
   font-size: 150px;
  margin-left: 55px;
  color: cadetblue;
}
.os{

}
.os::after{
  content: 'o';
  font-size: 150px;
  margin-left: 55px;
  color: black;
}
.xs{

}
.xs::after{
  content: 'x';
   font-size: 150px;
  margin-left: 55px;
  color: black;
}
</style>