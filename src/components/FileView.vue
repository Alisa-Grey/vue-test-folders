<template>
  <div class="file-wrap" tabindex="0">
    <span class="file-avatar"></span>
    <p class="file">{{name}}</p>
  </div>
</template>

<script>
export default {
  name: 'FileView',
  props: {
    name: String
  }
}
</script>

<style scoped lang="scss">
.file-wrap {
  display: flex;
  align-items: center;
  outline: none;
  cursor: pointer;
  transition: all .2s ease-in-out;

  &:focus {
    outline: 1px solid #9966cc;
    outline-offset: 3px;
  }

  &:hover {
    filter: contrast(140%);
  }

  &:active {
    transform: scale(1.1);
    outline: none;
  }
}

.file-avatar {
  display: inline-block;
  width: 50px;
  height: 50px;
  background-image: url(../img/file.svg);
  background-size: contain;
}

.file {
  margin: 0;
  color: #1a0415;
}
</style>
