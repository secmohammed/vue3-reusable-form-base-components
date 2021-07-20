<script lang="tsx">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BaseCheckBox',
  props: {
    label: {
      required: true,
      type: String,
      default: '',
    },
    modelValue: {
      type: Boolean,
      default: false,
    },
  },
  setup(props, { emit }) {
    const handleInputChange = (e: Event) => {
      emit('update:modelValue', (e.target as HTMLInputElement).checked);
    };
    return () => (
      <>
        <input type="checkbox" checked={props.modelValue} onChange={handleInputChange} class="field" />
        {props.label && <label>{props.label}</label>}
      </>
    );
  },
});
</script>
