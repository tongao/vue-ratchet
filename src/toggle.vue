<template>
	<div class="toggle" :class="{'active': model}"><div class="toggle-handle" v-on:click="toggle"></div></div>
</template>

<script>
	export default {
		name: 'toggle',
		props:{
      model:{
        type: Boolean,
        twoWay: true,
        default: false
      }
    },

    methods: {
    	 toggle: function(){
            this.model = !this.model;
       }
    }
	}
</script>

<style lang="sass">
@import './scss/variables';
@import './scss/mixins';
.toggle {
  position: relative;
  display: block;
  width: 74px;
  height: 30px;
  background-color: #fff;
  border: 2px solid #ddd;
  border-radius: 20px;
  @include transition-property(background-color, border);
  @include transition-duration(.2s);

  // Sliding handle
  .toggle-handle {
    position: absolute;
    top: -1px;
    left: -1px;
    z-index: 2;
    width: 28px;
    height: 28px;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 100px;
    -webkit-transition-property: -webkit-transform, border, width;
       -moz-transition-property: -moz-transform, border, width;
            transition-property: transform, border, width;
    @include transition-duration(.2s);
  }
  &:before {
    position: absolute;
    top: 3px;
    right: 11px;
    font-size: 13px;
    color: #999;
    text-transform: uppercase;
    content: "Off";
  }

  // Active state for toggle
  &.active {
    background-color: $positive-color;
    border: 2px solid $positive-color;

    .toggle-handle {
      border-color: $positive-color;
      @include transform(translate3d(44px,0,0));
    }
    &:before {
      right: auto;
      left: 15px;
      color: #fff;
      content: "On";
    }
  }
  // Hide the checkbox
  input[type="checkbox"] {
    display: none;
  }
}
</style>
