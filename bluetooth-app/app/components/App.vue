<template>
    <Page>
      <StackLayout>
        <Button text="Ligar Bluetooth" @tap="onBluetooth" ></Button>

        <Label :text="textOn" />
      </StackLayout>
    </Page>
</template>
  


<script >
  var bluetooth = require("nativescript-bluetooth");
  
  export default {
    data() {
      return {
        textOn: 'Desligado'
      }
    },
    methods:{
      onBluetooth() {
        var that = this;
        bluetooth.requestCoarseLocationPermission().then(
          function(granted) {
            bluetooth.enable().then(
              function(enabled) {
                that.textOn = 'ok'
              }
            ).catch(err => console.log(err));
          }
        );
      }
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
        padding: 10
    }

  Label{
    vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
  }

    Button {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #e40b0b;
    }
</style>
