<template>
	<div>
	<button type="button" class="btn btn-primary" @click="onShareScreen">Share</button>
	<vue-webrtc ref="webrtc"
                      width="100%"
                      :roomId="roomId"
                      socketURL='http://192.168.1.112:4500/api/freelancer-ke/videochat/'
                      v-on:joined-room="logEvent"
                      v-on:left-room="logEvent"
                      v-on:open-room="logEvent"
                      v-on:share-started="logEvent"
                      v-on:share-stopped="logEvent"
                      @error="onError" />
                 
              </div>

</template>


<script>



export default {

	data(){
		return {
			roomId:"shshshs"
		}
	},
	methods: {
      onCapture() {
        this.img = this.$refs.webrtc.capture();
      },
      onJoin() {
        this.$refs.webrtc.join();
      },
      onLeave() {
        this.$refs.webrtc.leave();
      },
      onShareScreen() {
        this.img = this.$refs.webrtc.shareScreen();
      },
      onError(error, stream) {
        console.log('On Error Event', error, stream);
      },
      logEvent(event) {
        console.log('Event : ', event);
      },
    }

}

</script>

