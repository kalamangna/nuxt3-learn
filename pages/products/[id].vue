<template>
  <div>

    <Head>
      <Title>Nuxt Dojo | {{ product.title }}</Title>
      <Meta name="description" :content="product.description" />
    </Head>

    <ProductDetails :product="product" />
  </div>
</template>

<script setup>
const route = useRoute()
const { id } = route.params

const { data: product } = await useFetch(`https://fakestoreapi.com/products/${id}`)

if (!product.value) {
  throw createError({ statusCode: 404, statusMessage: 'Product not found', fatal: true })
}

definePageMeta({
  layout: 'products'
})

</script>

<style scoped>

</style>