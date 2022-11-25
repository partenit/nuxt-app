<template>
  <div>
    <header>
      <nav>
        <ul style="display: inline-block; list-style: none;">
          <li><NuxtLink to="/">Главная</NuxtLink></li>
          <li><NuxtLink to="/categories">Категории</NuxtLink></li>
        </ul>
      </nav>
    </header>
    <slot />
  </div>
</template>