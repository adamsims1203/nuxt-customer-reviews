<template>
  <div>
    Todo: CustomerReviews
    <pre>{{ reviews }}</pre>

    <p class="mb-10">Working Result:</p>

    <div class="inline-flex flex-col sm:flex-row justify-center items-center">
      <div>
        <img class="mx-auto" src="https://i.ibb.co/CbyNTCd/mark.png" />
      </div>
      <div
        class="
          w-0
          h-0
          border-r-[20px]
          border-r-transparent
          border-b-[20px]
          border-b-brand-10
          border-l-[20px]
          border-l-transparent
          sm:border-t-[20px]
          sm:border-t-transparent
          sm:border-r-[20px]
          sm:border-r-brand-10
          sm:border-l-[0px]
          sm:border-b-[20px]
          sm:border-b-transparent
        "
      ></div>
      <div
        class="
          bg-brand-10
          py-2
          px-4
          inline-flex
          flex-col
          items-center
          self-center
        "
      >
        <p class="font-bold text-black-75 leading-4">Das sagen unsere Kunden</p>
        <p class="flex justify-center">
          <star
            v-for="index in 5"
            :key="index"
            :type="rating(index)"
            class="drop-shadow-md"
          >
          </star>
        </p>
        <p class="font-bold text-black-75 leading-4">
          {{ `${reviews.fb_avg}/5 (aus ${reviews.fb_count} Bewertungen)` }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import star from './star.vue';

export default {
  name: 'CeCustomerReviews',
  extends: CeText,
  data() {
    return {
      reviews: {
        fb_count: '195',
        fb_avg: '4.5',
      },
    };
  },
  methods: {
    rating(index) {
      const avg = parseFloat(this.reviews.fb_avg);
      const floor = Math.floor(avg);
      if (index <= floor) return 1;
      if (index > floor + 1) return -1;
      if (avg < floor + 0.5) return -1;
      if (avg >= floor + 0.5) return 0;
    },
  },
};
</script>
