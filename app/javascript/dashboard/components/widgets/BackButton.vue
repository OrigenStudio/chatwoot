<script setup>
import router from '../../routes/index';
const props = defineProps({
  backUrl: {
    type: [String, Object],
    default: '',
  },
  buttonLabel: {
    type: String,
    default: '',
  },
  compact: {
    type: Boolean,
    default: false,
  },
});

const goBack = () => {
  if (props.backUrl !== '') {
    router.push(props.backUrl);
  } else {
    router.go(-1);
  }
};

const buttonStyleClass = props.compact ? 'text-sm' : 'text-base';
</script>

<template>
  <button
    class="flex items-center p-0 font-normal cursor-pointer text-n-slate-11"
    :class="buttonStyleClass"
    @click.capture="goBack"
  >
    <fluent-icon icon="chevron-left" class="-ml-1" />
    {{ buttonLabel || $t('GENERAL_SETTINGS.BACK') }}
  </button>
</template>
