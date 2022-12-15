<script>
import AppLayout from '@/Layouts/AppLayout.vue';
import {Link} from "@inertiajs/inertia-vue3";

export default {
  components: {
  AppLayout,
  Link
  },
  props: {
  note: Object
  },
  data() {
  return {
    form: {
    excerpt: this.note.excerpt,
    content: this.note.content
    }
  }
  },
  methods: {
  submit() {
    this.$inertia.put(this.route('notes.update',this.note.id),this.form)
  },
  destroy() {
    if(confirm('Are you sure you want to delete the record?'))
    {
    this.$inertia.delete(this.route('notes.destroy',this.note.id))
    }
  }
  }
}
</script>

<template>
  <AppLayout title="Dashboard">
  <template #header>
    <h2 class="font-semibold text-xl text-gray-800 leading-tight">
    Notas
    </h2>
  </template>
  <div class="py-12">
    <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
    <div class="md:grid md:grid-cols-3 md:gap-6">
      <div class="md:col-span-1">
      <div class="px-4 sm:px-0">
        <h3 class="text-lg text-gray-900">Notes Edit</h3>
        <p class="text-sm text-gray-600">This actions not rollback option!</p>
      </div>
      </div>
      <div class="md:col-span-2 mt-5 md:mt-0">
      <div class="shadow bg-white md:rounded-md p-4">
        <form @submit.prevent="submit">
        <label class="block font-medium text-sm text-gray-900" style="font-weight: bold"> Abstract </label>
        <textarea class="form-input w-full rounded-md shadow-sm" v-model="form.excerpt"></textarea>
        <label class="block font-medium text-sm text-gray-900" style="font-weight: bold"> Content </label>
        <textarea class="form-input w-full rounded-md shadow-sm" v-model="form.content" rows="12"></textarea>
        <button class="font-bold py-2 px-4 rounded-md bg-blue-500" style="margin: 10px"> Edit </button>
        <button class="font-bold py-2 px-4 rounded-md bg-red-400" style="margin: 10px">
          <a href="#" @click.prevent="destroy"> Delete </a>
        </button>
        </form>
      </div>
      </div>
    </div>
    </div>
  </div>
  </AppLayout>
</template>
