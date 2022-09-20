<template>
    <button class="shanY-button" :class="classes" :disabled="disabled">
        <span v-if="loading" class="shanY-loadingIndicator"></span>
        <slot />
    </button>
</template>
<script lang="ts">
import { computed } from 'vue';

export default {
    props: {
        theme: {
                type:String,
                default:'button'
        },
        size: {
            type: String,
                default:"normal"
        },
        level: {
            type: String,
                default:'normal'
        },
        disabled: {
            type: Boolean,
                default:false
        },
        loading: {
            type: Boolean,
                default:false
            }
    },
    setup(props) {
        const { theme, size,level } =props
        const classes = computed(() => {
            return {
                [`shanY-theme-${theme}`]: theme,
                [`shanY-size-${size}`]: size,
                [`shanY-level-${level}`]: level
            };
        })
        return {classes}
        }
    }
</script>
<style lang="scss">
    $h:32px;
    $border-color:#d9d9d9;
    $color:#333;
    $blue:#86bd6d;
    $radius:4px;
    $red:rgb(239,98,13);
    $grey: rgb(107, 107, 133);
    .shanY-button{
        box-sizing: border-box;
        height: $h;
        padding: 0 12px;
        cursor:pointer;
        display: inline-flex;
        justify-content: center;
        align-items: center;
        white-space: nowrap;
        background: white;
        color: $color;
        border:1px solid $border-color;
        border-radius: $radius;
        box-shadow: 0 1px 0 fade-out($color: #000000, $amount: 0.95);
        transition: background 250ms;
        &+&{
            margin-left:8px ;
        }
        &:hover,
        &:focus{
            color:$blue;
            border-color: $blue;
        }
        &:focus{
            outline: none;
        }
        &::-moz-focus-inner{
            border:0;
        }
        &.shanY-theme-link{
    border-color: transparent;
    box-shadow: none;
    color: $blue;
    &:hover,&:focus{
      color: lighten($blue, 15%);
    }
  }
  &.shanY-theme-text{
    border-color: transparent;
    box-shadow: none;
    color: inherit;
    &:hover,&:focus{
      background: darken(white, 5%);
    }
  }

    &.shanY-size-big{
        font-size: 24px;
        height: 48px;
        padding: 0 16px;
        margin-bottom: 20px;
    }
    &.shanY-size-small{
        font-size: 12px;
        height: 20px;
        padding: 0 4px;

    }
    &.shanY-theme-button {
    &.shanY-level-main {
      background: $blue;
      color: white;
      border-color: $blue;
      &:hover,
      &:focus {
        background: darken($blue, 10%);
        border-color: darken($blue, 10%);
      }
    }
    &.shanY-level-danger {
      background: $red;
      border-color: $red;
      color: white;
      &:hover,
      &:focus {
        background: darken($red, 10%);
        border-color: darken($red, 10%);
      }
    }
  }
  &.shanY-theme-link {
    &.shanY-level-danger {
      color: $red;
      &:hover,
      &:focus {
        color: darken($red, 10%);
      }
    }
    &.shanY-level-main {
      color: $blue;
      &:hover,
      &:focus {
        color: darken($blue, 10%);
        font-size: 20px;
      }
    }
  }
  &.shanY-theme-text {
    &.shanY-level-main {
      color: $blue;
      &:hover,
      &:focus {
        color: darken($blue, 10%);
      }
    }
    &.shanY-level-danger {
      color: $red;
      &:hover,
      &:focus {
        color: darken($red, 10%);
      }
    }
  }
  &.shanY-theme-button {
    &[disabled] {
      cursor: not-allowed;
      color: $grey;
      background:rgb(238, 236, 236) ;
      &:hover {
        border-color: $grey;
        background: rgb(226, 226, 226);
      }
    }
  }
  &.shanY-theme-link, &.shanY-theme-text {
    &[disabled] {
      cursor: not-allowed;
      color: $grey;
      background:rgb(226, 226, 226) ;
    }
  }
  >.shanY-loadingIndicator{
    width: 12px;
    height: 12px;
    display: inline-block;
    margin-right:4px ;
    border-radius: 12px;
    border-color: $blue $blue $blue transparent;
    border-style: solid;
    border-width: 2px;
    animation: shanY-spin 1s infinite linear;
  }
    }
    @keyframes shanY-spin{
        0%{transform: rotate(0deg);}
        100%{transform: rotate(360deg);}
    }
</style>