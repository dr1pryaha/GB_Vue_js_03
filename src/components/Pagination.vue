<template>
  <ul class="pagination">
    <li class="pagination-item">
      <button
        type="button"
        @click="onClickFirstPage"
        :disabled="isInFirstPage"
        aria-label="Go to first page"
      >
        First
      </button>
    </li>

    <li class="pagination-item">
      <button
        type="button"
        @click="onClickPreviousPage"
        :disabled="isInFirstPage"
        aria-label="Go to previous page"
      >
        Previous
      </button>
    </li>

    <li v-for="(page, idx) in pages" :key="idx" class="pagination-item">
      <button
        type="button"
        @click="onClickPage(page.name)"
        :disabled="page.isDisabled"
        :class="{ active: isPageActive(page.name) }"
        :aria-label="`Go to page number ${page.name}`"
      >
        {{ page.name }}
      </button>
    </li>

    <li class="pagination-item">
      <button
        type="button"
        @click="onClickNextPage"
        :disabled="isInLastPage"
        aria-label="Go to next page"
      >
        Next
      </button>
    </li>

    <li class="pagination-item">
      <button
        type="button"
        @click="onClickLastPage"
        :disabled="isInLastPage"
        aria-label="Go to last page"
      >
        Last
      </button>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Pagination",
  props: {
    maxVisibleButtons: {
      type: Number,
      required: false,
      default: 5,
    },
    pageCount: {
      type: Number,
      required: true,
    },
    perPage: {
      type: Number,
      required: true,
    },
    currentPage: {
      type: Number,
      required: true,
    },
    costsList: {
      type: Array,
      required: true,
    },
    size: {
      type: Number,
      required: false,
      default: 3,
    },
  },

  computed: {
    startPage() {
      if (this.currentPage === 1 || this.currentPage === this.pageCount) {
        return 1;
      }

      return this.currentPage - 1;
    },
    endPage() {
      return Math.min(
        this.startPage + this.maxVisibleButtons - 1,
        this.pageCount
      );
    },
    pages() {
      const range = [];

      for (let i = this.startPage; i <= this.endPage; i += 1) {
        range.push({
          name: i,
          isDisabled: i === this.currentPage,
        });
      }

      return range;
    },
    isInFirstPage() {
      return this.currentPage === 1;
    },
    isInLastPage() {
      return this.currentPage === this.pageCount;
    },
  },
  methods: {
    onClickFirstPage() {
      this.$emit("onPageChange", 1);
    },
    onClickPreviousPage() {
      this.$emit("onPageChange", this.currentPage - 1);
    },
    onClickPage(page) {
      this.$emit("onPageChange", page);
    },
    onClickNextPage() {
      this.$emit("onPageChange", this.currentPage + 1);
    },
    onClickLastPage() {
      this.$emit("onPageChange", this.pageCount);
    },
    isPageActive(page) {
      return this.currentPage === page;
    },
  },
};
</script>

<style lang="scss">
.pagination {
  list-style-type: none;

  &-item {
    display: inline-block;
    margin: 5px;
  }
}

.active {
  background-color: cadetblue;
  color: #ffffff;
}
</style>
