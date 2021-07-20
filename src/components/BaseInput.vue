<script lang="tsx">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BaseInput',
  props: {
    label: {
      required: true,
      type: String,
      default: '',
    },
    modelValue: {
      type: [String, Number],
      default: '',
    },
  },
  setup(props, { attrs, emit }) {
    const handleInputChange = (e: Event) => {
      emit('update:modelValue', e.target.value);
    };
    return () => (
      <>
        <label>{props.label}</label>
        <input value={props.modelValue} onInput={handleInputChange} {...attrs} placeholder={props.label} class="field" />
      </>
    );
  },
});
</script>
