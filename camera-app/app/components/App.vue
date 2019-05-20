<template>
    <Page>
        <ActionBar title="Camera!"/>
        <StackLayout>
			<Button text="Take Picture" @tap="takePicture" />
			<Image :src="img" width="75" height="75" />
        </StackLayout>
    </Page>
</template>

<script>
import * as camera from "nativescript-camera";

export default {
	data() {
		return {
			img:''
		}
	},
	methods:{
		takePicture() {
			camera.requestPermissions()
			.then(() => {
				camera.takePicture({ width: 300, height: 300, keepAspectRatio: true, saveToGallery:true })
				.then(imageAsset => {
					this.img = imageAsset;
				})
				.catch(e => {
					console.log('error:', e);
				});
			})
			.catch(e => {
				console.log('Error requesting permission');
			});
		}
	}
}
</script>