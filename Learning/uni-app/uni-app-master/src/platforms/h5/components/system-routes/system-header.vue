<template>
  <div class="system-header">
    <div class="header-text">
      <slot />
    </div>
    <div
      class="header-btn header-back uni-btn-icon header-btn-icon"
      @click="_back"
    >
      &#xe601;
    </div>
    <div
      v-if="confirm"
      class="header-btn header-confirm"
      @click="_confirm"
    >
      <svg
        class="header-btn-img"
        width="200px"
        height="200.00px"
        viewBox="0 0 1024 1024"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path d="M939.6960642844446 226.08613831111114c-14.635971697777777-13.725872355555557-37.719236835555556-13.070208568888889-51.445109191111115 1.6029502577777779L402.69993870222225 744.6571451733333 137.46159843555557 483.31364238222227c-14.344349013333334-14.12709944888889-37.392384-13.98030904888889-51.51948344888889 0.3640399644444444-14.12709944888889 14.30911886222222-13.945078897777778 37.392384 0.40122709333333334 51.482296319999996l291.8171704888889 287.48392106666665c0.10960327111111111 0.10960327111111111 0.2544366933333333 0.1448334222222222 0.3640399644444444 0.2544366933333333s0.1448334222222222 0.2544366933333333 0.2544366933333333 0.3640399644444444c2.293843057777778 2.1842397866666667 5.061329351111111 3.4231500799999997 7.719212373333333 4.879309937777777 1.3113264355555554 0.7652670577777777 2.43867648 1.8926159644444445 3.822419057777778 2.43867648 4.2960634311111106 1.6753664 8.846562417777779 2.548279751111111 13.361832391111111 2.548279751111111 4.769706666666666 0 9.539412195555554-0.9472864711111111 13.98030904888889-2.839903573333333 1.4933469866666664-0.6184766577777778 2.6578830222222223-1.8926159644444445 4.0416267377777775-2.6950701511111115 2.7302991644444448-1.6029502577777779 5.5702027377777785-2.9495068444444446 7.901232924444444-5.315766044444445 0.10960327111111111-0.10960327111111111 0.1448334222222222-0.2916238222222222 0.2544366933333333-0.40122709333333334 0.07241614222222222-0.10960327111111111 0.21920654222222222-0.1448334222222222 0.3268528355555555-0.2544366933333333L941.2579134577779 277.5273335466667C955.0953460622222 262.9305059555556 954.3320359822221 239.8844279466666 939.6960642844446 226.08613831111114z" />
      </svg>
    </div>
  </div>
</template>
<script>
export default {
  name: 'SystemHeader',
  props: {
    confirm: {
      type: Boolean,
      default: false
    }
  },
  created () {
    document.title = this.$slots.default[0].text
    UniServiceJSBridge.emit('onNavigationBarChange', {
      titleText: document.title,
      textColor: '#fff',
      backgroundColor: '#000'
    })
  },
  methods: {
    _back () {
      this.$emit('back')
    },
    _confirm () {
      this.$emit('confirm')
    }
  }
}
</script>

<style>
  .system-header {
    position: relative;
    width: 100%;
    height: 44px;
    color: #fff;
    background-color: black;
    padding: 0 44px;
    text-align: center;
    line-height: 44px;
    font-size: 16px;
    box-sizing: border-box;
  }

  .system-header * {
    box-sizing: border-box;
  }

  .header-text {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .header-btn {
    position: absolute;
    width: 44px;
    height: 44px;
    top: 0;
  }

  .header-btn-img {
    fill: #fff;
    width: 50%;
    height: 50%;
    margin: 25%;
  }

  .header-back {
    left: 0;
  }

  .header-confirm {
    right: 0;
  }

  .header-btn-icon {
    font-size: 27px;
    line-height: 44px;
  }
</style>
