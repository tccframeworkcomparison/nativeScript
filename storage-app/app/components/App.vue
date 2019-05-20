<template>
    <Page>
        <ActionBar title="Welcome to NativeScript-Vue!"/>
        <StackLayout columns="*" rows="*">
          
            <Button text="SALVAR" @tap="saveData"/>
            <TextField v-model="text" hint="Enter text..." />
            <Label class="message" :text="msg" col="0" row="0"/>
       
        </StackLayout>
    </Page>
</template>

<script >
  let LS = require( "nativescript-localstorage" );
   
  export default {
    data() {
      return {
        msg: '',
        text: null,
      }
    },
    methods: {
      saveData(){
        LS.setItem('text', this.text);
        this.msg = LS.getItem('text')
        this.text = null
      }
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
</style>
