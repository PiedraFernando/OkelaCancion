<script>
export default {
  data() {
    return {
      idVideo: '',
      sleepVideo: 5,
      player: null
    }
  },
  methods: {
    onYouTubeIframeAPIReady() {
      this.player = new YT.Player('player', {
        height: '360',
        width: '640',
        videoId: this.idVideo,
        events: {
          onStateChange: this.pauseVideo,
        },
      });
    },
    pauseVideo(e) {
      if (e.data === 1) {
        console.log("emepezo");
        setTimeout(() => {
          this.player.pauseVideo();
        }, this.sleepVideo * 1000);
      }
    }
  },
  mounted() {
  }
}
</script>

<template>
  <div class="container vh-100">
    <h1 class="text-center text-light mb-3 mt-3">Okela Canción</h1>
    <div class="row">
      <div class="col-sm-12 col-md mt-3">
        <label for="idVideo" class="text-light text-center w-100 mb-2">ID video</label>
        <input v-model="idVideo" type="text" id="idVideo" class="form-control">
      </div>
      <div class="col-sm-12 col-md d-flex justify-content-center mt-3">
        <button type="button" class="btn btn-primary" @click="onYouTubeIframeAPIReady">Reproducir
          video</button>
      </div>
      <div class="col-sm-12 col-md mt-3">
        <label for="sleepVideo" class="text-light text-center w-100 mb-2">Pausar cada (segundos)</label>
        <input v-model.number="sleepVideo" type="text" id="sleepVideo" class="form-control">
      </div>
    </div>

    <div class="d-flex justify-content-center mt-5">
      <div id="player"></div>
    </div>
  </div>
  <div><p class="text-light text-center">Pagina creada por <a href="https://github.com/PiedraFernando" target="_blank" rel="noopener noreferrer">PiedraFernando</a></p></div>
</template>