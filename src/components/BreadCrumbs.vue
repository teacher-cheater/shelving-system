<template>
  <nav class="breadcrumb" aria-label="breadcrumb">
    <ol>
      <li><a href="/">Главная</a></li>
      <li><a href="/storage-systems">Системы хранения</a></li>
      <li aria-current="page">Комплекты стеллажных систем</li>
    </ol>
  </nav>
</template>

<style scoped>
.breadcrumb ol {
  display: flex;
  row-gap: 10px;
  column-gap: 30px;
  flex-wrap: wrap;
}

.breadcrumb ol li {
  position: relative;
}

.breadcrumb ol li a {
  color: rgb(130, 130, 130);
}

.breadcrumb ol li:not(:last-child)::after {
  content: "";
  position: absolute;
  display: block;
  top: 1px;
  right: -17px;
  width: 2px;
  height: 95%;
  background-color: rgb(130, 130, 130);
  transform: rotate(19deg);
}
</style>
