<template>
  <div class="storybook  storybook-button"> 
    <NuxtLink :class="classes" @click="onClick" :style="style">
     <slot></slot>
    </NuxtLink>
 </div>
</template>

<script lang="ts" setup>
import './button.css';
import { computed } from 'vue';

type Sizes = 'small' | 'medium' | 'large' | 'xlarge';

const props = withDefaults(defineProps<{
  
  primary?: boolean,
  /**
   * size of the button
   */
  size?: Sizes ,
  /**
   * background color of the button
   */
  backgroundColor?: string,

  dataTestid ?: string

}>(), { primary: false });

const emit = defineEmits<{
  (e: 'click', id: number): void;
}>();

const classes = computed(() => ({
  'storybook-button': true,
  'storybook-button--primary': props.primary,
  'storybook-button--secondary': !props.primary,
  [`storybook-button--${props.size || 'medium'}`]: true,
}));

const style = computed(() => ({
  backgroundColor: props.backgroundColor
}));

const onClick = () => {
  emit("click", 1)
};

</script>