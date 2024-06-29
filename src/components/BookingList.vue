<template>
  <section>
    <h2> Here's your current booking:</h2>

    <div class="row" v-for="(booking, index) in bookings" :key="index">
        <div> {{ booking.cabin }} </div>
    </div>

    <h3 class="row">
        Total: {{ totalDisplay }}
    </h3>
  </section>
</template>

<script>
export default {
    props: { //NOTE - We're expecting an array of information about bookings, so we'll declare our prop as type Array
        bookings: Array
    },

    computed: { //NOTE - computed properties to automatically calculate values
        totalDisplay() {
            let totalCost = 0;
            if (this.bookings && this.bookings.length > 0) {
                totalCost = this.bookings.map(b => b.price).reduce((a, b) => a + b);
            }
            return '$ ' + totalCost.toLocaleString();
        }
    }
}
</script>

<style>

</style>