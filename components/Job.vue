<template>
  <div class="boreer-b-2 border-t-2 border-gray-200 p-4 pb-2 flex justify-between group"
  :class="{ 'bg-blue-200': job.hightlighted }">
    <img :src="job.company_logo" :alt="`${job.company_name} logo`" class="h-12 w-12 mr-4">

    <div class="flex flex-wrap items-center justify-between w-full">
      <div class="w-full md:w-4/12 mr-2">
        <div class="flex items-center mr-1" v-if="job.pinned">
          <svg class="w-4 h-4 text-yellow-500" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
            <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
          </svg>
          <h2 class="font-bold leading-none">{{job.job_title}}</h2>
        </div>


        <a href="#" class="text-sm">{{job.company_name}}</a>

        <div class="flex items-center">
          <svg class="w-4 h-4 text-gray-600" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M18 13V5a2 2 0 00-2-2H4a2 2 0 00-2 2v8a2 2 0 002 2h3l3 3 3-3h3a2 2 0 002-2zM5 7a1 1 0 011-1h8a1 1 0 110 2H6a1 1 0 01-1-1zm1 3a1 1 0 100 2h3a1 1 0 100-2H6z" clip-rule="evenodd" />
          </svg>
          <div class="text-sm text-gray-600">
            {{job.job_location}}
          </div>
        </div>
      </div>

      <div class="w-full md:w-4/12 mb-2">
        <nuxt-link :to="{name: 'tags-slug', params: { slug: tag.slug}}" class="inline-block text-gray-600 border-2 border-gray-300 px-3 py-1 rounded-lg mr-2 bg-white"
          v-for="tag in job.tags" :key="tag.slug">{{tag.title}}</nuxt-link>
      </div>

      <div class="mb-2">
        <div class="opacity-100 md:opacity-0 group-hover:opacity-100 transition-opacity duration-200">
          <a :href="job.job_link" class="inline-block border-2 border-blue-400 text-blue-400
            font-bold rounded-lg px-3 py-2 bg-white">Apply fpr this job</a>
        </div>
      </div>

    </div>
  </div>
</template>




<script>

export default {
  props:{
    job: {
      required: true,
      type: Object
    }
  }

}
</script>

