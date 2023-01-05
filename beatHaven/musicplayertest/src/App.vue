<template>
  <v-app dark>
    <v-content>
      <v-container>
        <v-btn @click="updateData()"></v-btn>
        <player-title-bar></player-title-bar>
        <v-spacer></v-spacer>
        <player-playlist-panel style="top:30px;" :playlist="playlist" />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import PlayerTitleBar from "./components/PlayerTitleBar.vue";
import PlayerPlaylistPanel from "./components/PlayerPlaylistPanel.vue";
import {Howl} from 'howler'

export default {
  name: "App",

  components: {
    PlayerTitleBar,
    PlayerPlaylistPanel,
  },
  data: () => ({
    userInput: '',
    playlist: [
      {title: "I Feel It Coming", artist: "The Weeknd", howl: null, display: true, duration: "00:00"},
      {title: "I Feel It Coming", artist: "The Weeknd", howl: null, display: true},
      {title: "I Feel It Coming", artist: "The Weeknd", howl: null, display: true}
    ]
  }),
  methods: {
    updateData() {
    this.playlist.forEach ((track) => {
      let file = track.title.replace(/\s/g, "_")
      console.log(`./playlist/${file}.mp3`)
      track.howl = new Howl({
        src: [`./playlist/${file}.mp3`],
        preload: ['metadata']
      })
      track.howl.once('load', function(){
        track.duration = track.howl._duration
      })
      console.log(track.duration)
    })
  }
  },
  created() {
    this.updateData();
  },

};
</script>
