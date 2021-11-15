<template>
  <v-footer class="footer rounded-t-xl">
    <v-row class="my-0">
      <v-col cols="12">
        <LpLogo />
      </v-col>
      <v-col cols="12">
        <p
          class="
            footer__text
            d-block
            text-center
            font-weight-light
            text-caption
          "
        >
          &copy; {{ new Date().getFullYear() }} LocalPaper. All rights reserved.
        </p>
      </v-col>
      <v-col cols="12">
        <p
          class="footer-text mx-auto text-center font-weight-light text-caption"
        >
          LocalPaper, LLC a Delaware limited liability company and its
          affiliates (“LocalPaper”) is not a registered broker-dealer,
          investment advisor or crowdfunding portal. LocalPaper does not endorse
          any of the opportunities that appear on this website over any other
          opportunity available to an accredited investor (the “LocalPaper
          Marketplace”), nor does it make any recommendations regarding the
          appropriateness of particular opportunities for any investor. No
          communication by LocalPaper through this website or any other medium,
          should be construed or is intended to be a recommendation to purchase,
          sell or hold any security or otherwise to be investment, tax,
          financial, accounting, legal, regulatory or compliance advice. Nothing
          on this website is intended as an offer to extend credit, an offer to
          purchase or sell securities or a solicitation of any securities
          transaction. Investment opportunities on the LocalPaper Marketplace
          are speculative and involve substantial risk. You should not invest
          unless you can sustain the risk of loss of capital, including the risk
          of total loss of capital. Private placement investments are NOT bank
          deposits (and thus NOT insured by the FDIC or by any other federal
          governmental agency), are NOT guaranteed by LocalPaper or any other
          party, and MAY lose value. Neither the Securities and Exchange
          Commission nor any federal or state securities commission or
          regulatory authority has recommended or approved any investment or the
          accuracy or completeness of any of the information or materials
          provided by or through the website.
        </p>
      </v-col>
    </v-row>
  </v-footer>
</template>
<script>
import LpLogo from './LpLogo.vue'
export default {
  name: 'LpFooter',
  components: { LpLogo },
}
</script>
<style scoped>
.footer {
  background: var(--lp-background) !important;
}
.footer__text {
  color: #c7c8ca;
}
</style>
