<template>
  <div class="px-6 py-3 min-w-600 overflow-hidden overflow-x-auto align-middle sm:rounded-md">
    <table class="min-w-full border divide-y divide-gray-200">
      <thead>
      <tr>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase">ID</span>
        </th>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase">Название</span>
        </th>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase">Описание</span>
        </th>
      </tr>
      </thead>

      <tbody class="bg-white divide-y divide-gray-200 divide-solid">
      <template v-for="item in items" :key="item.id">
        <tr class="bg-white">
          <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap">
            {{ item.id }}
          </td>
          <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap">
            {{ item.name }}
          </td>
          <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap">
            {{ item.description }}
          </td>
        </tr>
      </template>
      </tbody>
    </table>
  </div>
</template>

<script setup>
  import {useFetch} from "nuxt/app";

  const response = await useFetch('https://test-shop.estater.biz/api/v1/categories')
  const items = response.data._rawValue.data

</script>