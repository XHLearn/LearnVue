<template>
  <iframe :src="swaggerUIUrl" width="100%" height="800px" frameborder="0"></iframe>
</template>

<script>
export default {
  name: 'SwaggerUIComponent',
  data() {
    return {
      swaggerUIUrl: 'http://localhost:8080' // 替换为你的 Swagger UI 服务器地址
    };
  }
};
</script>
