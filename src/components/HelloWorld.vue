<template>
  <div class="hello">

  <router-link   :to="{path: '/about'}" >
    <a class="btn btn-xs btn-danger">About </a>
  </router-link>

    <h1>{{ msg }}</h1>
   <button @click="incrementCounter()">Increment</button>{{counter}}<br>
    <input type="text" v-model="myDataProperty"/><br/>
    <input :value="myDataProperty" @input="updateMyProperty($event)"/>
   {{fullName}}
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue,Watch } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  counter=1;
  firstName='';
  lastName='';
  myDataProperty='';
  //@Prop() private myDataProperty!: string;
  //@Prop() private counter: number=1;
  //@Prop() private firstName!: String;
  //@Prop() private lastName!: String;

  
  // Component method
  updateMyProperty ($event) {
    this.myDataProperty = $event.target.value
  }
  incrementCounter() {
    console.log('incrementing')
    this.counter++
  }

  //Computed value
  get fullName() {
      return this.firstName+' '+this.lastName
  }

  //Vue event life cyle
  created() {
   // console.log(this.mixinValue) // -> Hello
    this.firstName='Fred'
    this.lastName='Jones'
  }

  mounted() {
    console.log('mounted ')
  }

  //Watching an object 
  @Watch('msg')
  onPropertyChanged(value: string, oldValue: string) {
    // Do stuff with the watcher here.
  }



}
</script>