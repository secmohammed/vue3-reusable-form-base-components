<script lang="tsx">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BaseSelect',
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
    options: {
      type: Array,
      required: true,
    },
  },
  setup(props, { attrs, emit }) {
    const handleInputChange = (e: Event) => {
      emit('update:modelValue', (e.target as HTMLSelectElement).value);
    };
    return () => (
      <>
        { props.label && <label>{ props.label }</label>}
        <select value={props.modelValue} class="field" onChange={handleInputChange} {...attrs}>
          {props.options.map((option) => (
            <option
              value={option as string}
              key={option as string}
              selected={option === props.modelValue}
            >
              {option}
            </option>
          ))}
        </select>
      </>
    );
  },
});
</script>
