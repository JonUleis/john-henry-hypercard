<template>
  <div id="app" :class="{ playing: playing, mobile: isMobile().any }">
    <header>
      <span v-if="isMobile().any">
        Turn your device sideways to enjoy.
      </span>
    </header>
    <div class="hypercard">
      <nav class="bar">
        <span>John_Henry_Sampler.stk</span>
      </nav>
      <div class="main">
        <div class="tracks" v-if="!info">
          <a
            class="btn"
            :class="{
              'btn--active': isMobile().any && playing && current == i
            }"
            v-for="(track, i) in tracks"
            :key="track[0]"
            @click="play(i)"
          >
            <img :src="require(`@/assets/titles/${track[1]}.png`)" />
            <span>{{ track[0] }}</span></a
          >
        </div>
        <div class="info" v-else>
          <p>
            This stack is freeware. Please copy and distrubute it if you think
            that that would be a good thing to do. Please copy the entire thing
            including this information if you do copy it.
          </p>
          <p>
            A debt of gratitude is owed to Mr. Fumitaka Anzai for his<br />
            "Poly Music" stack, which was liberally employed as an aid in the
            creation of these tiny versions of our songs. We also used two of
            the samples in his stack.
          </p>
          <p>
            all songs published by They Might Be Giants Music<br />
            administered by WB Music Corp.<br />
            publ. &amp; ©1994 Elektra Entertainment
          </p>
          <p>
            If the music on this program sounds too messed up, it may be that
            it's playing incorrectly (though perhaps not). If this is the case,
            allocating more memory to Hypercard (in the bottom right corner of
            Hypercard's "Get Info" window) may improve the situation.
          </p>
          <a class="btn btn--cool" @click="info = false"><span>Cool</span></a>
        </div>
        <a
          class="btn btn--home"
          href="https://www.theymightbegiants.com/john-henry"
          target="_blank"
        />
        <a class="btn btn--about" @click="info = true"
          ><span>About This Stack</span></a
        >
      </div>
    </div>
    <footer>
      <span
        >HTML5 Version by
        <a href="https://jonuleis.com/" target="_blank">Jon Uleis</a>. Code on
        <a
          href="https://github.com/JonUleis/john-henry-hypercard"
          target="_blank"
          >GitHub</a
        >. <br />
        Thanks
        <a href="http://mikebuffington.net/" target="_blank">Mike Buffington</a>
        and
        <a href="http://tmbg.bryceland.com/JHstack.php" target="_blank"
          >Bryce Hurst</a
        >.</span
      >
    </footer>
  </div>
</template>

<script>
import { Howl } from "howler";
import isMobile from "ismobilejs";

export default {
  name: "app",
  data() {
    return {
      playing: false,
      sound: undefined,
      current: 0,
      info: false,
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
    isMobile,
    play(file) {
      this.playing = true;
      this.current = file;
      if (this.sound) {
        this.sound.unload();
      }
      this.sound = new Howl({
        html5: true,
        autoplay: true,
        src: `audio/${this.tracks[file][1]}.mp3`,
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
