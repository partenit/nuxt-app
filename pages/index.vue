<template>
  <div class="px-6 py-3 min-w-600 overflow-hidden overflow-x-auto align-middle sm:rounded-md">
    <table class="min-w-full border divide-y divide-gray-200">
      <thead>
      <tr>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase"></span>
        </th>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase">Название</span>
        </th>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase">Описание</span>
        </th>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase">Цена</span>
        </th>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase">Код</span>
        </th>
        <th class="px-6 py-3 bg-gray-50">
                    <span
                        class="text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase">Категория</span>
        </th>
      </tr>
      </thead>

      <tbody class="bg-white divide-y divide-gray-200 divide-solid">
        <template v-for="item in items" :key="item.id">
          <tr class="bg-white">
            <td class="text-sm leading-5 text-gray-900 whitespace-no-wrap">
              <img src="https://picsum.photos/100" style="width:100px;"/>
            </td>
            <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap">
              {{ item.name }}
            </td>
            <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap">
              {{ item.description }}
            </td>
            <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap">
              {{ item.price }}
            </td>
            <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap">
              {{ item.code }}
            </td>
            <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap">
              {{ item.category.name }}
            </td>
          </tr>
        </template>
      </tbody>
    </table>
  </div>

  <TailwindPagination
      :data="items_data"
      @pagination-change-page="getResults"
  />
</template>

<script setup>
  import {useFetch} from "nuxt/app";
  import { TailwindPagination } from 'laravel-vue-pagination';

  let items = {};
  const items_data = ref({});

  const getResults = async (page = 1) => {
    const response = await useFetch(`https://test-shop.estater.biz/api/v1/products?page=${page}`)
    items = response.data._rawValue.data
    items_data.value = response.data._rawValue
  }

  getResults();

/*  const response = await useFetch('https://test-shop.estater.biz/api/v1/products')
  const items = response.data._rawValue.data*/

</script>