<script lang="tsx">
import { defineComponent, reactive } from 'vue';
import BaseInput from '@/components/BaseInput.vue';
import BaseSelect from '@/components/BaseSelect.vue';

export default defineComponent({
  components: {
    BaseInput,
    BaseSelect,
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
            <input type="radio" v-model={state.event.pets} value="1" name="pets" />
            <label>Yes</label>
          </div>

          <div>
            <input type="radio" v-model={state.event.pets} value="0" name="pets" />
            <label>No</label>
          </div>

          <h3>Extras</h3>
          <div>
            <input type="checkbox" v-model={state.event.extras.catering} class="field" />
            <label>Catering</label>
          </div>

          <div>
            <input type="checkbox" v-model={state.event.extras.music} class="field" />
            <label>Live music</label>
          </div>

          <button class="button -fill-gradient" type="submit">Submit</button>
        </form>
      </div>
    );
  },
});
</script>
