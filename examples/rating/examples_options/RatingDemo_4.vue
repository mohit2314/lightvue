<template>
  <div>
    <h3>Capture rating value with events</h3>
    <h5>On mouse click</h5>
    <lv-rating :show-rating="true" @update:rating="rating = $event"></lv-rating>
    <div style="margin-top: 10px; font-weight: bold">
      {{ currentRatingText }}
    </div>

    <h5>On mouse hover</h5>
    <div @mouseleave="mouseOverRating = null" style="display: inline-block">
      <lv-rating :show-rating="true" @hover:rating="mouseOverRating = $event" :increment="0.5"></lv-rating>
    </div>
    <div style="margin-top: 10px; font-weight: bold">
      {{ mouseOverRatingText }}
    </div>

    <h2>Resetable stars with v-model</h2>
    <div style="display: inline-block">
      <!-- <lv-rating v-model:rating="resetableRating"></lv-rating> -->
      <div style="padding-top: 10px; cursor: pointer; margin-bottom: 20px; color: blue">
        <a @click="resetableRating = 0">Reset Rating</a>
      </div>
    </div>
  </div>
</template>

<script>
import LvRating from 'lightvue/rating';
export default {
  components: {
    LvRating,
  },
  methods: {
    showCurrentRating(rating) {
      this.currentSelectedRating = rating === 0 ? this.currentSelectedRating : 'Click to select ' + rating + ' stars';
    },
    setCurrentSelectedRating(rating) {
      this.currentSelectedRating = 'You have Selected: ' + rating + ' stars';
    },
  },
  computed: {
    currentRatingText() {
      return this.rating ? 'You have selected ' + this.rating + ' stars' : 'No rating selected';
    },
    mouseOverRatingText() {
      return this.mouseOverRating ? 'Click to select ' + this.mouseOverRating + ' stars' : 'No Rating';
    },
  },
  data() {
    return {
      rating: null,
      resetableRating: 2,
      currentRating: 'No Rating',
      mouseOverRating: null,
    };
  },
};
</script>
