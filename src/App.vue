<!-- App.vue -->
<template>
  <div id="app">
    <h1>Aiera EventList</h1>
    <iframe height="575" width="375" id="example_iframe1"></iframe>
  </div>
</template>

<script>
import { onMounted } from 'vue'
import { Aiera } from 'aiera-sdk'

const isinArray = [
  'US0378331005', // Apple Inc.
  'US02079K1079', // Alphabet Inc. (Google)
  'US5949181045', // Microsoft Corporation
  'US0231351067', // Amazon.com Inc.
  'US30303M1027', // Facebook, Inc.
  'US88160R1014', // Tesla, Inc.
  'US67066G1040', // NVIDIA Corporation
  'US0846707026', // Berkshire Hathaway Inc.
  'US92826C8394', // Visa Inc.
  'US46625H1005', // JPMorgan Chase & Co.
  'US4581401001', // Intel Corporation
  'US17275R1023', // Cisco Systems, Inc.
  'US7427181091', // Procter & Gamble Company
  'US5801351017', // McDonald's Corporation
  'US91324P1021', // UnitedHealth Group Incorporated
  'US2546871060', // Walt Disney Company
  'US1912161007', // Coca-Cola Company
  'US6541061031', // Nike, Inc.
  'US7170811035', // Pfizer Inc.
  'US5486611073', // Lowe's Companies, Inc.
  'US4370761029', // Home Depot, Inc.
  'US9497461015', // Wells Fargo & Company
  'US1101221083', // Bristol-Myers Squibb Company
  'US7181721090', // Philip Morris International Inc.
  'US0605051046', // Bank of America Corporation
  'US1667641005', // Chevron Corporation
  'US38141G1040', // Goldman Sachs Group, Inc.
  'US5949724083', // Micron Technology, Inc.
  'US4592001014', // International Business Machines Corporation
  'US2605661048', // Dow Inc.
  'US9311421039', // Walmart Inc.
  'US4781601046', // Johnson & Johnson
  'US8552441094', // Starbucks Corporation
  'US2786421030', // eBay Inc.
  'US7134481081', // PepsiCo, Inc.
  'US58933Y1055', // Merck & Co., Inc.
  'US1270971039', // Caterpillar Inc.
  'US2193501051', // Corning Incorporated
  'US2310211063', // Cummins Inc.
  'US1729674242', // Citigroup Inc.
  'US1011371077', // Boston Scientific Corporation
  'US0970231058', // Boeing Company
  'US6174464486', // Morgan Stanley
  'US0758871091', // Becton, Dickinson and Company
  'US2441991054', // Deere & Company
  'US3755581036', // Gilead Sciences, Inc.
  'US03027X1000', // American Tower Corporation
  'US00724F1012', // Adobe Inc.
  'US9029733048', // U.S. Bancorp
  'US2473617023', // Delta Air Lines, Inc.
  'US4932671088', // KeyCorp
  'US09247X1019', // BlackRock, Inc.
  'US4595061015', // International Paper Company
  'US4448591028', // Humana Inc.
  'US7134481081', // PepsiCo, Inc.
  'US1491231015', // Caterpillar Inc.
  'US2193501051', // Corning Incorporated
  'US2310211063', // Cummins Inc.
  'US1729674242', // Citigroup Inc.
  'US1011371077', // Boston Scientific Corporation
  'US0970231058', // Boeing Company
  'US6174464486', // Morgan Stanley
  'US0758871091', // Becton, Dickinson and Company
  'US2441991054', // Deere & Company
  'US3755581036', // Gilead Sciences, Inc.
  'US03027X1000', // American Tower Corporation
  'US00724F1012', // Adobe Inc.
  'US9029733048', // U.S. Bancorp
  'US2473617023', // Delta Air Lines, Inc.
  'US4932671088', // KeyCorp
  'US09247X1019', // BlackRock, Inc.
  'US4595061015', // International Paper Company
  'US4448591028', // Humana Inc.
  'US7134481081', // PepsiCo, Inc.
  'US1491231015', // Caterpillar Inc.
  'US2193501051', // Corning Incorporated
  'US2310211063', // Cummins Inc.
  'US1729674242', // Citigroup Inc.
  'US1011371077', // Boston Scientific Corporation
  'US0970231058', // Boeing Company
  'US6174464486', // Morgan Stanley
  'US0758871091', // Becton, Dickinson and Company
  'US2441991054', // Deere & Company
  'US3755581036', // Gilead Sciences, Inc.
  'US03027X1000', // American Tower Corporation
  'US00724F1012', // Adobe Inc.
  'US9029733048', // U.S. Bancorp
  'US2473617023', // Delta Air Lines, Inc.
  'US4932671088', // KeyCorp
  'US09247X1019', // BlackRock, Inc.
  'US4595061015', // International Paper Company
  'US4448591028', // Humana Inc.
  'US7134481081', // PepsiCo, Inc.
  'US1491231015', // Caterpillar Inc.
  'US2193501051', // Corning Incorporated
  'US2310211063', // Cummins Inc.
  'US1729674242', // Citigroup Inc.
  'US1011371077', // Boston Scientific Corporation
  'US0970231058', // Boeing Company
  'US6174464486', // Morgan Stanley
  'US0758871091', // Becton, Dickinson and Company
  'US2441991054' // Deere & Company
]

export default {
  name: 'App',
  setup() {
    onMounted(() => {
      const eventList = new Aiera.Module(
        // 'http://localhost:8000/modules/EventList/index.html', for local testing
        'https://public.aiera.com/aiera-sdk/0.0.75/modules/EventList/index.html',
        'example_iframe1'
      )

      eventList.load().then(() => {
        eventList.authenticateApiKey('9b9a25ca85b41fb3c136f9814e7e8105')
      })

      eventList.on('authenticated', () => {
        eventList.configure({
          hideSettings: true,
          options: {
            showCompanyFilter: true
          },
          tracking: {
            userId: '123abc'
          }
        })
      })

      eventList.on('configured', () => {
        eventList.setWatchlist(isinArray.map((ISIN) => ({ ISIN })))
      })
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
