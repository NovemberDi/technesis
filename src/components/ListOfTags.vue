<template>
  <div class="list-of-tags" ref="el">
    <div class="list-of-tags__tag" v-for="(tag, index) in listForTags" :key="index">
      <template v-if="!tag.divider">
        <p class="list-of-tags__tag__text">
          {{ tag.text }}
        </p>
        <div class="list-of-tags__tag__icon">
          <v-icon large color="blue darken-2">{{ tag.icon }}</v-icon>
        </div>
      </template>
      <template v-else>
        <v-icon>mdi-circle-small</v-icon>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListOfTags',
  props: {
    tags: Array,
    alignment: {
      type: String,
      default: 'left'
    }
  },
  methods: {
    cutter() {
      let arr = this.$refs.el.childNodes;
      for (let i = arr.length - 1; i >= 0; i--) {
        arr[i].classList.remove('hiden')
      }
      if (arr.length < 1) return
      for (let i = arr.length - 1; i >= 0; i--) {
        if ((Math.floor(this.$refs.el.getBoundingClientRect().right)) < Math.floor(arr[i].lastChild.getBoundingClientRect().right)) {
          arr[i].classList.add('hiden');
          if ((i - 1) > 0) {
            arr[i - 1].classList.add('hiden');
          }
        }
      }
    }


  },
  mounted() {
    this.cutter();
    window.addEventListener('resize', this.cutter)
  },
  computed: {
    align() {
      if (this.alignment == 'width') return 'space-between'
      return 'flex-start'
    },
    listForTags() {
      let arr = [];
      this.tags.forEach((item, index, array) => {
        arr.push(item);
        if (index < array.length - 1) {
          arr.push({ divider: true })
        }
      })
      return arr
    }
  }
}
</script>

<style scoped lang="scss">
.list-of-tags {
  position: relative;
  width: 100%;
  max-width: auto;
  height: 100%;
  border: 1px solid #333333;
  border-radius: 8px;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: v-bind(align);

  & .list-of-tags__tag {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 8px;
    margin-right: 8px;
  }

  & .hiden {
    display: none;
  }

  & .list-of-tags__tag__text {
    margin: 0;
    align-items: center;
    justify-content: center;
    align-items: center;
    height: fit-content;
    white-space: nowrap;
  }

  & .list-of-tags__tag__icon {
    margin-left: 10px;
  }
}
</style>
