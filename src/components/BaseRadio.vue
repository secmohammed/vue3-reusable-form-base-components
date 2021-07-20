<script lang="tsx">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BaseInput',
  props: {
    label: {
      type: String,
      default: '',
    },
    modelValue: {
      type: [String, Number],
      default: '',
    },
    value: {
      type: [String, Number],
      required: true,
    },
  },
  setup(props, { emit, attrs }) {
    const handleInputChange = () => {
      emit('update:modelValue', props.value);
      emit('modelValueUpdated', props.value);
    };
    return () => (
      <>
        <input
          type="radio"
          onChange={handleInputChange}
          checked={props.modelValue === props.value}
          value={props.value}
          {...attrs}
        />
        {props.label && <label>{props.label }</label>}
      </>
    );
  },
});
</script>
