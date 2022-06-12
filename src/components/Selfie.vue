<template>
	<div>
		<video ref="video" @canplay="initCanvas()">Stream Unavailable</video>
		<button @click="takePicture()">Take A Picture</button>
		<canvas ref="canvas" style="display: none;"/>
	</div>
</template>

<script>
export default {
	name: 'Selfie',
	mounted() {
		this.canvas = this.$refs.canvas
		this.video = this.$refs.video
		this.startCapture()
	},
	methods: {
		startCapture() {
			navigator.mediaDevices.getUserMedia({video: true, audio: false}).then(stream => {
				this.video.srcObject = stream
				this.video.play()
			}).catch(error => {
				console.log(error)
			})
		},
		takePicture() {
			let context = this.canvas.getContext('2d')
			context.drawImage(this.video, 0, 0, this.video.videoWidth, this.video.videoHeight)
			this.$emit('picture-taken', this.canvas.toDataURL('image/png'))
		},
		initCanvas() {
			this.canvas.setAttribute('width', this.video.videoWidth)
			this.canvas.setAttribute('height', this.video.videoHeight)
		}
	},
	data() {
		return {
			canvas: null,
			video: null
		}
	}
}
</script>

<style scoped>
	
</style>