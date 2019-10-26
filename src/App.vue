<template>
  <div id="app" :class="{ playing: playing }">
    <div class="hypercard">
      <nav class="bar">
        <span>John_Henry_Sampler.stk</span>
      </nav>
      <div class="main">
        <div class="tracks">
          <a
            class="btn"
            v-for="track in tracks"
            :key="track[0]"
            @click="play(track[1])"
            ><span>{{ track[0] }}</span></a
          >
        </div>
        <a class="btn btn--home" />
        <a class="btn btn--about" />
      </div>
    </div>
  </div>
</template>

<script>
import { Howl } from "howler";

export default {
  name: "app",
  data() {
    return {
      playing: false,
      sound: undefined,
      tracks: [
        ["A Self Called Nowhere", "self"],
        ["I Should Be Allowed To Think", "think"],
        ["O, Do Not Forsake Me", "forsake"],
        ["Spy", "spy"],
        ["No One Knows My Plan", "plan"],
        ["Why Must I Be Sad", "sad"],
        ["Meet James Ensor", "ensor"],
        ["Nyquil Driver", "nyquil"],
        ["Out Of Jail", "jail"],
        ["Unrelated Thing", "thing"],
        ["Thermostat", "thermostat"],
        ["Snail Shell", "snail"],
        ["Stomp Box", "stomp"],
        ["The End of the Tour", "tour"],
        ["Window", "window"],
        ["Sleeping in the Flowers", "flowers"],
        ["Destination Moon", "moon"],
        ["Extra Savior-Faire", "extra"],
        ["Dirtbike", "dirtbike"],
        ["Subliminal", "subliminal"]
      ]
    };
  },
  methods: {
    play(file) {
      if (this.sound) {
        this.sound.unload();
      }
      this.sound = new Howl({
        html5: true,
        autoplay: true,
        src: `audio/${file}.mp3`,
        onplay: () => {
          this.playing = true;
          this.update();
        },
        onend: () => {
          this.playing = false;
        }
      });
    }
  }
};
</script>

<style lang="scss">
@import "main.scss";
</style>
