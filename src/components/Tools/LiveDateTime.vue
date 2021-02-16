<template>
  <div class="text-subtitle-1 ml-4 mt-2">
    {{ date }}
  </div>
</template>

<script>
import moment from 'moment';

export default {
  data() {
    return {
      date: '',
    }
  },
  methods: {
    getDate() {
      this.date = moment(new Date()).format("MMMM DD, h:mm:ss a");
      setTimeout(this.getDate, 1000);
    },
  },
  mounted() {
    this.getDate();
  }
}
</script>
