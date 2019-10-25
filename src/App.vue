<template>
  <div id="app">
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
export default {
  name: "app",
  data() {
    return {
      tracks: [
        ["A Self Called Nowhere", "self"],
        ["I Should Be Allowed To Think", "allowed"],
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
  }
};
</script>

<style lang="scss">
@import "main.scss";
</style>
