<template>
  <svg
    clip-rule="evenodd"
    fill-rule="evenodd"
    stroke-linejoin="round"
    stroke-miterlimit="2"
    version="1.1"
    viewBox="0 0 12 12"
    xml:space="preserve"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:serif="http://www.serif.com/"
    class="close-filter close-icon"
    v-bind:style="{ 
      width: iconSize, 
      height: iconSize, 
      marginTop: iconMargins[0], 
      marginRight: iconMargins[1], 
      marginBottom: iconMargins[2], 
      marginLeft: iconMargins[3], 
    }"
  >
    <g transform="matrix(.70711 -.70711 .70711 .70711 -3.4281 6)">
      <g serif:id="User-Item-/-Normal">
        <g serif:id="User-Item/Atoms/CTA/Pending">
          <g serif:id="Icons-/-Close">
            <path
              d="m6.667 1.111c0.201 0 0.366 0.159 0.376 0.358v0.019 4.802h4.803c0.208 0 0.376 0.169 0.376 0.377 0 0.201-0.158 0.366-0.358 0.376h-0.018-4.803v4.803c0 0.208-0.168 0.376-0.376 0.376-0.202 0-0.367-0.158-0.377-0.358v-0.018-4.803h-4.802c-0.208 0-0.377-0.168-0.377-0.376 0-0.202 0.159-0.367 0.358-0.377h0.019 4.802v-4.802c0-0.208 0.169-0.377 0.377-0.377z"
              fill="#fff"
            />
          </g>
        </g>
      </g>
    </g>
  </svg>
</template>

<script>
export default {
  name: "CloseIcon",
  props: ['size', 'margins'],
  data() {
    return {
      iconSize: this.size?? '14px',
      iconMargins: this.margins?? ['20px', '0px', '20px', '20px']
    }
  }
};
</script>

<style>
.close-filter{
  filter: invert(46%) sepia(50%) saturate(517%) hue-rotate(174deg) brightness(92%) contrast(86%);
}
.close-icon{
  margin:20px 0px 20px 20px;
}
</style>