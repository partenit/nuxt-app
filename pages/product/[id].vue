<template>
  <div class="mt-6">
    <h1 class="text-5xl">
      {{ item.name }}
    </h1>
  </div>

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
      </tbody>
    </table>
  </div>
</template>

<script setup>
import {useRoute} from "nuxt/app";
import {useFetch} from "nuxt/app";

const route = useRoute()
const response = await useFetch(`https://test-shop.estater.biz/api/v1/product/${route.params.id}`)
const item = response.data._rawValue

</script>