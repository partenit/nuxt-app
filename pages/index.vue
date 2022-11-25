<template>
  <div class="mt-6">
    <h1 class="text-5xl">
      Главная. Продукты
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
        <template v-for="item in items" :key="item.id">
          <tr class="bg-white">
            <td class="text-sm leading-5 text-gray-900 whitespace-no-wrap">
              <img src="https://picsum.photos/100" style="width:100px;"/>
            </td>
            <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap" style="text-decoration: underline!important;">
              <NuxtLink :to="`/product/${item.slug}`" >{{ item.name }}</NuxtLink>
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
            <td class="px-6 py-4 text-sm leading-5 text-gray-900 whitespace-no-wrap" style="text-decoration: underline!important;">
              <NuxtLink :to="`/category/${item.category.slug}`">{{ item.category.name }}</NuxtLink>
            </td>
          </tr>
        </template>
      </tbody>
    </table>
  </div>

  <template v-for="item_ in pages" :key="item_">
    <NuxtLink :to="`/?page=${item_}`" :external="true">
      <button class="m-2 border-2" v-bind:class="{ 'font-medium': item_ == page }">
        {{ item_ }}
      </button >
    </NuxtLink>
  </template>

</template>

<script setup>
  import {useFetch, useRoute} from "nuxt/app"
  const route = useRoute()
  const items_data = ref({})
  const page = route.query.page ?? 1
  const response = await useFetch(`https://test-shop.estater.biz/api/v1/products?page=${page}`)
  const items = response.data._rawValue.data
  items_data.value = response.data._rawValue
  let pages = []

  for (let i = 1; i <= items_data.value.last_page; i++) {
    pages.push(i)
  }

</script>