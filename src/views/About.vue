<template>
  <div>
    <div class="onas">
      <div class="oProjektu">
        <p>S Jančou jsme se potkaly na Digitální akademii Web a taneční kurzy byly jednou z prvních věcí, o kterých jsme se spolu bavily. Zjistily jsme, že zorientovat se v nabídce brněnský tanečních škol je hrozně zdlouhavé. Každá škola má nabídku kurzů schovanou jinde a je nutné se tím vším balastem proklikat, přestože vlastně všude nabízejí podobné informace - místo, čas, nabídku tanců, zda je nutné mít partnera...</p>
      </div>

      <div class="janina">
        <img class="fotoJanina" src="@/Images/Janina medailonek_transparentni.png"></img>
        <p class="oJanine">V roce 2018 jsem zcela změnila obor a v současnosti pracuji v malé IT firmě na oddělení supportu (klientům i kolegům). Teď se chci naučit web, protože to je způsob komunikace a práce s lidmi, která mě prostě baví. S tím souvisí i UX, které mě zaujalo. Fotím na film a do budoucna bych se tomu chtěla věnovat více, řízeně padám na boulderu; Skotsko, káva a cestování (na motorce) jsou lásky na celý život, knihy čtu podruhé jen výjimečně, nerada prohrávám u deskovek, ale jinak se je nenaučím.</p>
      </div>

      <div class="janca">
        <img class="fotoJanca" src="@/Images/Jana medailonek_transparentni.png"></img>
        <p class="oJance">Jako neIT zaměstnanec v IT firmě jsem zjistila, jak to v takové firmě chodí a že se mi tam moc líbí. K tomu se přidala touha naučit se něco nového a cesta do Czechitas byla jasná. Miluji příběhy, jsem trochu perfekcionistka a velký dříč. Mám ráda zvířata a věci, které jsou užitečné, a ještě k tomu hezky vypadají. Poslední dobou mě táhne téma cirkulární ekonomiky, zero waste, minimalismus a UX. Ráda bych se vrátila ke hře na klavír a přidala k tomu i ukulele.
        </p>
      </div>
    </div>

    <ourfooter />

  </div>
</template>

<script>
import OurFooter from '../components/OurFooter.vue';
export default {
    components: {
      'ourfooter': OurFooter
    }
}
</script>

<style scoped>
p {
  color: #ffffff
}

.onas {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  color: white;
}

.oProjektu {
  flex-basis: 100%;
  font-size: 22px;
  padding: 20px;
}

.janina {
  flex: 0 1 40%;
  display: flex;
  flex-direction: column;
  align-items: center;
} 

.janca {
  flex: 0 1 40%;
  display: flex;
  flex-direction: column;
  align-items: center;
} 

.fotoJanina,
.fotoJanca {
  width: 200px;
} 

</style>