<template>
  <div class="home">
    <button type="button" name="button"
      class="pa5 ba bg-green white br3 ma3 center db pointer"
      @click="start">
    Start</button>
  </div>
</template>

<script>
import Tone from 'tone'
export default {
  name: 'home',
  mounted: function () {
    const synth = new Tone.Synth().toMaster()
    // synth.triggerAttackRelease('E4', '4n')
    const loop = new Tone.Loop(function (time) {
      synth.triggerAttackRelease('E2', '4n')
    }, '1n')

    const loop2 = new Tone.Loop(function (time) {
      synth.triggerAttackRelease('A2', '8n')
    }, '4n')

    // const loop3 = new Tone.Loop(function (time) {
    //   synth.triggerAttackRelease('A2', '8n')
    // }, '4n')

    loop.start('1m').stop('10m')
    loop2.start('4m').stop('10m')
  },
  methods: {
    start: function () {
      Tone.Transport.start()
    }
  }
}
</script>
