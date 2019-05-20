<template>
    <Page>
        <ActionBar title="Welcome to NativeScript-Vue!"/>
        <StackLayout columns="*" rows="*">
            <Button text="Ligar GPS" @tap="getLocation" ></Button>
            <Label class="message" :text="lat" col="0" row="0"/>
            <Label class="message" :text="long" col="1" row="1"/>
        </StackLayout>
    </Page>
</template>

<script >
  var geolocation = require("nativescript-geolocation");

  export default {
    data() {
      return {
        lat: "Latitude: ",
        long: "Longitude: "
      }
    },
    methods: {
      getLocation(){
        let that = this;
        geolocation.getCurrentLocation({
          maximumAge: 5000,
          timeout: 10000
        })
        .then(function (loc) {
          if (loc) {
              that.lat = "Latitude: "+loc.latitude;
              that.long = "Longitude: "+loc.longitude;
          }
        }, function (e) {
            console.log("Error: " + (e.message || e));
        }).catch(er => console.log(er));
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
