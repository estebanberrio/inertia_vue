<script>
import AppLayout from '@/Layouts/AppLayout.vue'

export default
{
  components:
  {
  AppLayout,

  },
  props:
  {
  notes:Array,
},
    data() {
        return {
            q: ''
        }
    },
    watch: {
        q: function (value) {
            this.$inertia.replace(this.route('notes.index',{q: value}))
        }
    }
}
</script>
<template>
  <AppLayout title="Dashboard">
  <template #header>
    <h2 class="font-semibold text-xl text-gray-800 leading-tight">
    Notes Module
    </h2>
    </template>
    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <div class="md:grid md:grid-cols-3 md:gap-6">
          <div class="md:col-span-1">
            <div class="p3-4 sm:px0">
              <h3 class="text-lg text-gray-900">Note List</h3>
              <p class="text-lg text-gray-900">aditional text</p>
            </div>
          </div>
          <div class="md:col-span-2 mt-5 md:mt-0">
            <div class="shadow bg-white md:rounded-md p-4">
              <div class="flex justify-between">
                <inertia-link class="bg-black text-white font-bold px-4 py-2 rounded-md" :href="route('notes.create')" >
                 Create
                </inertia-link>
                <input type="text" class="form-input rounded-md shadow-sm" placeholder="Search.." v-model="q">
              </div>
              <hr class="my-6">
              <table>
                <tr v-for="note in notes">
                  <td class="border 1px solid black px-4 py-2">
                    {{note.excerpt}}
                  </td>
                  <td class="border 1px solid black px-4 py-2">
                    <inertia-link :href="route('notes.show', note.id)">
                      Show
                    </inertia-link>
                  </td>
                  <td class="border 1px solid black px-4 py-2">
                    <inertia-link :href="route('notes.edit', note.id)">
                      Edit
                    </inertia-link>
                  </td>
                </tr>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </AppLayout>
</template>
