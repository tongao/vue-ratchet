<template>
	<div>
	 <ul class="segmented-control" role="tablist">
	        <a class="control-item"
	            v-for="r in renderData"
	            v-bind:class="{
	              'active': ($index === active),
	              'disabled': r.disabled
	            }"
	            @click.prevent="handleTabListClick($index, r)"
	            :disabled="r.disabled"
	        >
	            {{{r.header}}}
	        </a>
	 </ul>
	 <div class="card">
	    <slot></slot>
	 </div>
	</div>
</template>

<script>
  export default {
    props: {
      effect: {
        type: String,
        default: 'fadein'
      },
      active: {
        type: Number,
        default: 0
      }
    },
    data() {
      return {
        renderData: []
      }
    },
    methods: {
        handleTabListClick(index, el) {
            if (!el.disabled) this.active = index
        }
    }
  }
</script>

<style lang="sass">
	@import './scss/variables';
	@import './scss/mixins';
	.segmented-control {
  position: relative;
  display: table;
  overflow: hidden;
  font-size: 12px;
  font-weight: $font-weight-light;
  background-color: $chrome-color;
  border: 1px solid #ccc;
  border-radius: 3px;
  width:auto;
  // Section within controller
  .control-item {
    display: table-cell;
    width: 1%;
    padding-top: 6px;
    padding-bottom: 7px;
    overflow: hidden;
    line-height: 1;
    color: #333;
    text-align: center;
    text-overflow: ellipsis;
    white-space: nowrap;
    border-left: 1px solid #ccc;

    // Remove border-left and shadow from first section
    &:first-child {
      border-left-width: 0;
    }

    // Tap state of segmented controller
    &:active {
      background-color: #eee;
    }

    // Selected state of segmented controller
    &.active {
      background-color: #ccc;
    }
  }
}

// Other segmented controller types
// --------------------------------------------------

// Primary
.segmented-control-primary {
  border-color: $primary-color;

  .control-item {
    color: $primary-color;
    border-color: inherit;

    &:active {
      background-color: lighten($primary-color, 35%);
    }
    &.active {
      color: #fff;
      background-color: $primary-color;
    }
  }
}

// Positive
.segmented-control-positive {
  border-color: $positive-color;

  .control-item {
    color: $positive-color;
    border-color: inherit;

    &:active {
      background-color: lighten($positive-color, 35%);
    }
    &.active {
      color: #fff;
      background-color: $positive-color;
    }
  }
}

// Negative
.segmented-control-negative {
  border-color: $negative-color;

  .control-item {
    color: $negative-color;
    border-color: inherit;

    &:active {
      background-color: lighten($negative-color, 35%);
    }
    &.active {
      color: #fff;
      background-color: $negative-color;
    }
    a.disabled {
	    color: #777;
	}
  }
}

// This is used to by the js to show and hide content tide to the segmented control.
.control-content {
  &.active {
    display: block;
  }
}
</style>
