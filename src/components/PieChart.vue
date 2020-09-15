<template>
  <div class="pie-chart" :style="pieStyle"></div>
</template>

<script>
  export default {
    props: [
      'pieData'
    ],
    /*
      computed property, which generates dynamically the background style.
    */
    computed: {
      pieStyle() {
        /*
          Contains the sum of the last values.
        */
        let sum = 0;

        /*
          The map function creates new key => value pairs
          It's creates for each value this pattern, for example
          #fefefe 0 30%
          which is needed for the conic-gradient
        */
        let styles = this.pieData.map(
          piePart => `${piePart.color} 0 ${sum += piePart.value}%`
        );

        /*
          returns an object with the conic-gradient.
          The join method creates and returns a new string by concatenating 
          all of the elements in an array (or an array-like object), 
          separated by commas or a specified separator string. 
          If the array has only one item, 
          then that item will be returned without using the separator.
        */
        return { background: 'conic-gradient('+ styles.join(",") +')' };
      }
    }
  }
</script>

<style lang="scss" scoped>
  .pie-chart {
    width: 300px;
    height: 300px;
    border-radius: 50%;
    border: 2px solid #fefefe;
    animation: show 1s ease-in-out;
    /*
    The CSS Example - If you wanna have several pieces, 
    you can define for each piece a color, 
    second the position from the center, 
    in this case always zero. 
    And last how much angle should this section take.
    You should define the angle as an absolute value.
    Each piece is a different layer, that overlaps each other in a z-index.

    background: conic-gradient(
      #fefefe 0 30%,
      #fe0000 0 70%,
      #00fe00 0 100%
    );
    */
  }

  /*
    The rotating animation
  */
  @keyframes show {
    0% {
      transform: scale(0) rotate(720deg);
    }
    100% {
      transform: scale(1) rotate(0deg);
    }
  }
</style>