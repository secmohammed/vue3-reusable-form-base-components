<script lang="tsx">
import { defineComponent } from 'vue';
import BaseRadio from './BaseRadio.vue';

export default defineComponent({
  name: 'BaseInput',
  props: {
    options: {
      type: Array,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    modelValue: {
      type: [String, Number],
      required: true,
    },
    vertical: {
      type: Boolean,
      default: false,
    },
  },
  setup(props, { emit, attrs }) {
    const handleUpdateGroup = (e: Event) => {
      emit('update:modelValue', e);
    };
    return () => (
      <>
        {props.options.map((option: any) => (props.vertical ? <div key={option.value}>
            <BaseRadio
              label={option.label}
              value={option.value}
              {...attrs}
              /* @ts-ignore */
              name={props.name}
              modelValue={props.modelValue}
              onModelValueUpdated={handleUpdateGroup}
            />
          </div>
          : <span class="horizontal" key={option.value}>
            <BaseRadio
              label={option.label}
              value={option.value}
              {...attrs}
              /* @ts-ignore */
              name={props.name}
              modelValue={props.modelValue}
              onModelValueUpdated={handleUpdateGroup}
            />
          </span>))}
      </>
    );
  },
});
</script>
<style lang="scss" scoped>
  .horizontal {
    margin-right: 20px;
  }
</style>
