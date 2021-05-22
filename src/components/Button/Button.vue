<template>
    <input
      v-if="type"
      :class="classes" 
      :type="type"
      :value="value"
      @mouseover="onMouseover"
      @click="onClick"
    />

    <a
      v-else-if="href"
      :class="classes"
      :href="href"
      :target="target"
      @click="onClick"
      @mouseover="onMouseover"
    >
      <slot></slot>
    </a>

    <button
      v-else
      :class="classes"
      @mouseover="onMouseover"
      @click="onClick"
    > 
      <slot></slot>
    </button>
</template>

<script>
export default {
  name: 'Button',

  props: {
    type: {
      type: String,
      default: null,
    },

    href: {
      type: String,
      default: null,
    },

    target: {
      type: String,
      default: null,
      validator (value) {
        return [
          '_blank', //	Opens the linked document in a new window or tab
          '_self', //	Opens the linked document in the same frame as it was clicked (this is default)
          '_parent', //	Opens the linked document in the parent frame
          '_top', //	Opens the linked document in the full body of the window
          'framename', //	Opens the linked document in the named iframe
        ].indexOf(value) !== -1
      }
    },

    value: {
      type: String,
      required: false,
    },

    // Colors

    isPrimary: {
      type: Boolean,
      default: false,
    },

    isLink: {
      type: Boolean,
      default: false,
    },

    isInfo: {
      type: Boolean,
      default: false,
    },

    isSuccess: {
      type: Boolean,
      default: false,
    },

    isWarning: {
      type: Boolean,
      default: false,
    },

    isDanger: {
      type: Boolean,
      default: false,
    },

    isWhite: {
      type: Boolean,
      default: false,
    },

    isLight: {
      type: Boolean,
      default: false,
    },

    isDark: {
      type: Boolean,
      default: false,
    },

    isBlack: {
      type: Boolean,
      default: false,
    },

    isText: {
      type: Boolean,
      default: false,
    },

    isGhost: {
      type: Boolean,
      default: false,
    },

    // Sizes

    isSmall: {
      type: Boolean,
      default: false,
    },

    isNormal: {
      type: Boolean,
      default: false,
    },

    isMedium: {
      type: Boolean,
      default: false,
    },

    isLarge: {
      type: Boolean,
      default: false,
    },

    // Displays

    isFullwidth: {
      type: Boolean,
      default: false,
    },

    // Styles

    isInverted: {
      type: Boolean,
      default: false,
    },

    isOutlined: {
      type: Boolean,
      default: false,
    },

    isRounded: {
      type: Boolean,
      default: false,
    },
  },

  data: () => ({
    isFocused: false,
  }),

  computed: {
    classes () {
      return {
        'button': true,
        'is-white': this.isWhite,
        'is-light': this.isLight,
        'is-dark': this.isDark,
        'is-black': this.isBlack,
        'is-text': this.isText,
        'is-ghost': this.isGhost,
        'is-primary': this.isPrimary,
        'is-link': this.isLink,
        'is-info': this.isInfo,
        'is-success': this.isSuccess,
        'is-warning': this.isWarning,
        'is-danger': this.isDanger,
        'is-small': this.isSmall,
        'is-normal': this.isNormal,
        'is-medium': this.isMedium,
        'is-large': this.isLarge,
        'is-fullwidth': this.isFullwidth,
        'is-inverted': this.isInverted,
        'is-outlined': this.isOutlined,
        'is-rounded': this.isRounded,
        'is-focused': this.isFocused
      }
    },
  },

  methods: {
    onClick (e) {
      this.$emit('click', e)
    },

    onMouseover (e) {
      this.isFocused = true
      this.$emit('mouseover', e)
    },

    onMouseleave (e) {
      this.isFocused = false
      this.$emit('mouseleave', e)
    }
  }
}
</script>