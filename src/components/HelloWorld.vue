<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
   <button @click="incrementCounter()">Increment</button>{{counter}}

   {{fullName}}
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  //@Prop() private counter: number=1;
  counter=1;
  firstName='';
  lastName='';
  //@Prop() private firstName!: String;
  //@Prop() private lastName!: String;

  incrementCounter() {
    console.log('incrementing')
    this.counter++
  }

  //Computed value
  get fullName() {
      return this.firstName+' '+this.lastName
  }

  created() {
    console.log('created ')
    this.firstName='Fred'
    this.lastName='Jones'
  }

  mounted() {
    console.log('mounted ')
  }
}
</script>