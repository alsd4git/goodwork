<template>
    <div class="bg-white rounded shadow py-8 mt-8">
        <div class="flex flex-col items-center">
            <img :src="avatar" :alt="'Default avatar of ' + user.name" class="w-32 h-32 rounded-full">
            <div class="text-grey-darker text-2xl font-semibold py-4">
                {{user.name}}
            </div>
            <div class="">
                <file-upload :user="user" @image-loaded="updateImage"></file-upload>
            </div>
        </div>
        <form class="px-8 pt-6">
            <div class="mb-6">
                <label class="block text-grey-darker text-sm font-bold mb-2" for="username">
                    {{ 'Name' | localize }}
                </label>
                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker" id="username" type="text" placeholder="Nehal Hasnayeen">
            </div>
            <div class="mb-6">
                <label class="block text-grey-darker text-sm font-bold mb-2" for="title">
                    {{ 'Title at Goodwork' | localize }}
                </label>
                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker" id="title" type="text" placeholder="Developer">
            </div>
            <div class="mb-6">
                <label class="block text-grey-darker text-sm font-bold mb-2" for="title">
                    {{ 'Short Bio' | localize }}
                </label>
                <textarea class="shadow appearance-none resize-none border rounded w-full py-2 px-3 text-grey-darker" id="bio" type="text" rows="3" placeholder="About Yourself"></textarea>
            </div>
            <div class="mb-6">
                <label class="block text-grey-darker text-sm font-bold mb-2" for="timezone">
                    {{ 'Time Zone' | localize }}
                </label>
                <div class="relative">
                    <select class="shadow appearance-none border rounded w-full px-3 py-2 text-grey-darker bg-grey-lighter text-grey-darker" id="grid-state">
                        <template v-for="timezone in timezones">
                            <option :value="timezone">{{ timezone}}</option>
                        </template>
                    </select>
                    <div class="pointer-events-none absolute pin-y pin-r flex items-center px-2 text-grey-darker">
                    <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
                    </div>
                </div>
            </div>
            <div class="mb-6">
                <label class="block text-grey-darker text-sm font-bold mb-2" for="weekstart">
                    {{ 'First Day of the Week' | localize }}
                </label>
                <div class="relative">
                    <select class="shadow appearance-none border rounded w-full px-3 py-2 text-grey-darker bg-grey-lighter text-grey-darker" id="weekstart">
                        <option>Saturday</option>
                        <option>Sunday</option>
                        <option>Monday</option>
                        <option>Tuesday</option>
                        <option>Wednesday</option>
                        <option>Thursday</option>
                        <option>Friday</option>
                    </select>
                    <div class="pointer-events-none absolute pin-y pin-r flex items-center px-2 text-grey-darker">
                    <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
                    </div>
                </div>
            </div>
            <div class="mb-6">
                <label class="block text-grey-darker text-sm font-bold mb-2" for="weekstart">
                    {{ 'Preffered Language' | localize }}
                </label>
                <div class="relative">
                    <select class="shadow appearance-none border rounded w-full px-3 py-2 text-grey-darker bg-grey-lighter text-grey-darker" id="weekstart">
                        <template v-for="(locale, key) in locales">
                            <option :value="key">{{ locale }}</option>
                        </template>
                    </select>
                    <div class="pointer-events-none absolute pin-y pin-r flex items-center px-2 text-grey-darker">
                    <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
                    </div>
                </div>
            </div>
            <div class="mt-8">
                <button class="bg-teal hover:bg-teal-dark text-white font-bold p-4 rounded shadow hover:shadow-lg" type="button">
                    {{ 'Update' | localize }}
                </button>
                <div></div>
            </div>
        </form>
    </div>
</template>

<script>
import FileUpload from './../partials/fileUpload'
export default {
  name: 'Own',
  components: {FileUpload},
  props: ['user', 'timezones', 'locales'],
  data: () => ({
    avatar: null
  }),
  methods: {
    updateImage (imageUrl) {
      this.avatar = imageUrl
    }
  },
  mounted () {
    this.avatar = this.generateUrl(this.user.avatar)
  }
}
</script>
