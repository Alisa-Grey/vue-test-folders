<template>
  <div class="container">
    <div class="folder-wrap" tabindex="0" @click="toggleChildren">
      <span class="folder-avatar"></span>
      <p class="folder">{{ name }}</p>
    </div>
    <template v-for="folder in folders" v-bind:key="folder">
      <FolderView
        :name="folder.name"
        :folders="folder.folders"
        :files="folder.files"
        :v-bind="key"
        v-if="showChildren"
      />
    </template>
    <div class="files-container" v-if="showChildren">
      <template v-for="file in files" v-bind:key="file">
        <FileView :name="file.name"/>
      </template>
    </div>
  </div>
</template>

<script>
import FileView from "./FileView";
export default {
  name: "FolderView",
  components: { FileView },
  props: {
    name: String,
    folders: Array,
    files: Array,
  },
  data() {
      return { showChildren: false }
  },
  methods: {
    toggleChildren() {
      this.showChildren = !this.showChildren;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container {
  max-width: 80vw;
  margin: 0 auto;
  padding: 0 3vw;
  background-color: #fcfcfa;

  &:not(:first-child) {
    margin-bottom: 2vw;
  }

  &:first-child {
    margin-top: 2vw;
    padding-top: 2.5vw;
    padding-bottom: 2.5vw;
  }
}

.folder-wrap {
  display: flex;
  flex-wrap: nowrap;
  align-items: center;
  width: fit-content;
  margin-bottom: 1vw;
  cursor: pointer;
  transition-property: outline, filter, transform;
  transition-duration: .2s;
  transition-timing-function: ease-in-out;

  &:focus {
    outline: 1px solid #49052a;
    outline-offset: 3px;
  }

  &:hover {
    filter: brightness(1.2);
  }

  &:active {
    transform: scale(1.1);
    outline: none;
  }
}

.folder {
  color: #721046;
}

.folder-avatar {
  display: inline-block;
  width: 50px;
  height: 50px;
  margin-right: 1vw;
  background-image: url(../img/folder.svg);
  background-repeat: no-repeat;
}

.files-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  max-width: 80%;
}
</style>
