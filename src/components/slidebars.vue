<template>
  <div class="slidebars">
    <div class="slidebars-content" :style="slidebarsLeftStyle">
      <slot></slot>
    </div>
    <div v-if="value" class="slidebars-overlay" @click="$emit('input', false)"></div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Boolean,
      default: false
    },
    width: {
      type: Number,
      default: 340
    },
    bgColor: {
      type: String,
      default: "#313131"
    },
    transitionTime: {
      type: Number,
      default: 300
    },
    position: {
      type: String,
      default: "left",
      validator: val => ["right", "left"].includes(val)
    }
  },
  data() {
    return {
      visible: this.value
    };
  },
  computed: {
    slidebarsLeftStyle() {
      let width = this.width + "px";
      let transitionValue = this.value ? "0" : "-" + width;
      let styles = {
        width,
        backgroundColor: this.bgColor,
        transition: "all " + this.transitionTime / 1000 + "s"
      };
      styles[this.position] = transitionValue;
      return styles;
    }
  },
  watch: {
    value(val) {
      if (val) {
        this.visible = true;
      } else {
        setTimeout(() => {
          this.visible = false;
        }, this.transitionTime);
      }
    }
  }
};
</script>

<style lang="scss">
.slidebars {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.slidebars-content {
  position: absolute;
  width: 340px;
  top: 0;
  height: 100%;
  background-color: rgba(47, 162, 255, 0.2);
  z-index: 100;
  color: white;
  pointer-events: all;
}
.slidebars-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 50;
  cursor: pointer;
  pointer-events: all;
}
</style>
