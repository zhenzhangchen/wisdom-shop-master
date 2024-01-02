<template>
	<view>
		<view class="page-body">
			<view class="page-section page-section-gap">
				<map style="width: 100%; height: 500px;" :latitude="latitude" :longitude="longitude" :markers="covers">
				</map>
			</view>
		</view>
		<livepusher></livepusher>
	</view>
</template>
<script>
import livepusher from '@/components/live'
	export default {
		data() {
			return {
					id:0, // 使用 marker点击事件 需要填写id
					title: 'map',
					latitude: 39.909,
					longitude: 116.39742,
					covers: [{
						latitude: 39.909,
						longitude: 116.39742,
						iconPath: '../../../static/location.png'
					}, {
						latitude: 39.90,
						longitude: 116.39,
						iconPath: '../../../static/location.png'
					}]
				}
		},
		onReady() {
	            // 注意：需要在onReady中 或 onLoad 延时
	            this.context = uni.createLivePusherContext("livePusher", this);
	        },
		methods: {
	            statechange(e) {
	                console.log("statechange:" + JSON.stringify(e));
	            },
	            netstatus(e) {
	                console.log("netstatus:" + JSON.stringify(e));
	            },
	            error(e) {
	                console.log("error:" + JSON.stringify(e));
	            },
	            start: function() {
	                this.context.start({
	                    success: (a) => {
	                        console.log("livePusher.start:" + JSON.stringify(a));
	                    }
	                });
	            },
	            close: function() {
	                this.context.close({
	                    success: (a) => {
	                        console.log("livePusher.close:" + JSON.stringify(a));
	                    }
	                });
	            },
	            snapshot: function() {
	                this.context.snapshot({
	                    success: (e) => {
	                        console.log(JSON.stringify(e));
	                    }
	                });
	            },
	            resume: function() {
	                this.context.resume({
	                    success: (a) => {
	                        console.log("livePusher.resume:" + JSON.stringify(a));
	                    }
	                });
	            },
	            pause: function() {
	                this.context.pause({
	                    success: (a) => {
	                        console.log("livePusher.pause:" + JSON.stringify(a));
	                    }
	                });
	            },
	            stop: function() {
	                this.context.stop({
	                    success: (a) => {
	                        console.log(JSON.stringify(a));
	                    }
	                });
	            },
	            switchCamera: function() {
	                this.context.switchCamera({
	                    success: (a) => {
	                        console.log("livePusher.switchCamera:" + JSON.stringify(a));
	                    }
	                });
	            },
	            startPreview: function() {
	                this.context.startPreview({
	                    success: (a) => {
	                        console.log("livePusher.startPreview:" + JSON.stringify(a));
	                    }
	                });
	            },
	            stopPreview: function() {
	                this.context.stopPreview({
	                    success: (a) => {
	                        console.log("livePusher.stopPreview:" + JSON.stringify(a));
	                    }
	                });
	            }
	        },
			components:{
				livepusher
			}
	}
</script>

<style lang="scss">

</style>