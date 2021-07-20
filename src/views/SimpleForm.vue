<script lang="tsx">
import { defineComponent, reactive } from 'vue';
import BaseInput from '@/components/BaseInput.vue';
import BaseCheckBox from '@/components/BaseCheckBox.vue';
import BaseSelect from '@/components/BaseSelect.vue';
import BaseRadioGroup from '@/components/BaseRadioGroup.vue';

export default defineComponent({
  components: {
    BaseInput,
    BaseSelect,
    BaseCheckBox,
    BaseRadioGroup,
  },
  setup() {
    const state = reactive({
      categories: [
        'sustainability',
        'nature',
        'animal welfare',
        'housing',
        'education',
        'food',
        'community',
      ],
      event: {
        category: '',
        title: '',
        description: '',
        location: '',
        pets: 1,
        extras: {
          catering: false,
          music: false,
        },
      },
      petOptions: [
        { label: 'Yes', value: 1 },
        { label: 'No', value: 0 },
      ],

    });
    return () => (
      <div>
        <h1>Create an event</h1>
        <form>
          <BaseSelect label="Select Your Category" options={state.categories} v-model={state.event.category}/>

          <h3>Name & describe your event</h3>
          <BaseInput
            v-model={state.event.title}
            label="Title"
            // @ts-ignore
            type="text"
          />
          <BaseInput
            v-model={state.event.description}
            label="Description"
            // @ts-ignore
            type="text"
          />

          <h3>Where is your event?</h3>

          <BaseInput
            v-model={state.event.location}
            label="Location"
            // @ts-ignore
            type="text"
          />

          <h3>Are pets allowed?</h3>
          <div>
            <BaseRadioGroup v-model={state.event.pets} modelValue={state.event.pets} name="pets" options={state.petOptions} vertical />
          </div>

          <h3>Extras</h3>
          <div>
            <BaseCheckBox v-model={state.event.extras.catering} label="Catering" />
          </div>

          <div>
            <BaseCheckBox v-model={state.event.extras.music} label="Live Music" />
          </div>

          <button class="button -fill-gradient" type="submit">Submit</button>
        </form>

      </div>
    );
  },
});
</script>
