---
title:  Pokémon HP Activation Calculator
layout: post
permalink: /pokemon/HP-Activation-Calculator
categories: Pokémon
---
<style>
span{
  font-weight: bold;
}
p.title {
  font-weight: bold;
  font-size: 20px;
  margin-top: 5px;
  margin-bottom: 0;
}
</style>

<div>
  <label for="hp">HP</label>: <input id="hp" type="number" min="0" placeholder="HP Value">
</div>
<div id="output">
<p class="title">Berries:</p>
Sitrus Berry would activate at <span id="sitrusRange">0</span> HP and restore <span id="sitrusRestore">0</span> HP.<br/>
Figy Berry, Wiki Berry, Mago Berry, Aguav Berry, and Iapapa Berry would activate at <span id="berryRange">0</span> HP and restore <span id="berryRestore">0</span> HP.<br/>
Liechi Berry, Ganlon Berry, Salac Berry, Petaya Berry, Apicot Berry, Lansat Berry, Starf Berry, Micle Berry, or Custap Berry would activate at <span id="effectBerry">0</span> HP and get its effect.<br/>

<p class="title">Items:</p>
Life Orb would do <span id="lifeOrb">0</span> damage on attacks.<br/>
Leftovers would restore <span id="leftovers">0</span> HP at the end of the turn.<br/>
Black Sludge would do <span id="blackSludgeDamage">0</span> damage to non-Poison Pokémon at the end of the turn and restore <span id="blackSludgeRestore">0</span> HP to Poison Pokémon.<br/>
Sticky Barb would do <span id="stickyBarb">0</span> damage at the end of the turn.<br/>

<p class="title">Weather and Status:</p>
Hail and Sandstorm would do <span id="weather">0</span> damage at the end of the turn.<br/>
Poison would do <span id="poison">0</span> damage at the end of the turn.<br/>

<p class="title">Abilities:</p>
Solar Power would do <span id="solarPower">0</span> damage in sun at the end of the turn.<br/>
Rain Dish would restore <span id="rainDish">0</span> HP in rain at the end of the turn.<br/>
Ice Body would restor <span id="iceBody">0</span> HP in hail at the end of the turn.<br/>
Dry Skin would do <span id="drySkinDamage">0</span> damage in sun at the end of the turn and restore <span id="drySkinRestore">0</span> HP in rain at the end of the turn.<br/>
Volt Absorb and Water Absorb would restore <span id="absorb">0</span> HP when hit by a Water or Electric move respectively.<br/>
Regenerator would restore <span id="regenerator">0</span> HP on switch out.<br/>
Poison Heal would restore <span id="poisonHeal">0</span> HP at the end of the turn.<br/>
Bad Dreams would do <span id="badDreams">0</span> damage to sleeping Pokémon at the end of the turn.<br/>
Gluttony would activate at <span id="gluttony">0</span> HP and consume a berry.<br/>
Cheek Pouch would restore <span id="cheekPouch">0</span> HP after consuming a berry.<br/>
Zen Mode, Wimp Out, Emergency Exit, Shields Down and Schooling, and Beserk would activate below <span id="belowHalf">0</span> HP.<br/>

<p class="title">Move Effects:</p>
Bind, Clamp, Fire Spin, Infestation, Magma Storm, Sand Tomb, Snap Trap, Thunder Cage, Whirlpool, Wrap, G-Max Centiferno, and G-Max Sandblast would do <span id="binding">0</span> damage at the end of the turn.<br/>
G-Max Wildfire, G-Max Cannonade, and G-Max Vine Lash would do <span id="gmaxEffect"></span> damage at the end of the turn.
</div>

<script>
  // TODO: Handle Rippen doubling berry effects.
  // TODO: Handle Binding Band for binding moves.
  window.onload = function(){
    const hpForm = document.querySelector("#hp");
    const sitrusRangeSpan = document.querySelector("#sitrusRange");
    const sitrusRestoreSpan = document.querySelector("#sitrusRestore");
    const berryRangeSpan = document.querySelector("#berryRange");
    const berryRestoreSpan = document.querySelector("#berryRestore");
    const effectBerrySpan = document.querySelector("#effectBerry");
    const lifeOrbSpan = document.querySelector("#lifeOrb");
    const leftoversSpan = document.querySelector("#leftovers");
    const blackSludgeDamageSpan = document.querySelector("#blackSludgeDamage");
    const blackSludgeRestoreSpan = document.querySelector("#blackSludgeRestore");
    const stickyBarbSpan = document.querySelector("#stickyBarb");
    const weatherSpan = document.querySelector("#weather");
    const poisonSpan = document.querySelector("#poison");
    const solarPowerSpan = document.querySelector("#solarPower");
    const rainDishSpan = document.querySelector("#rainDish");
    const iceBodySpan = document.querySelector("#iceBody");
    const drySkinDamageSpan = document.querySelector("#drySkinDamage");
    const drySkinRestoreSpan = document.querySelector("#drySkinRestore");
    const absorbSpan = document.querySelector("#absorb");
    const regeneratorSpan = document.querySelector("#regenerator");
    const poisonHealSpan = document.querySelector("#poisonHeal");
    const badDreamsSpan = document.querySelector("#badDreams");
    const gluttonySpan = document.querySelector("#gluttony");
    const cheekPouchSpan = document.querySelector("#cheekPouch");
    const belowHalfSpan = document.querySelector("#belowHalf");
    const bindingSpan = document.querySelector("#binding");
    const gmaxEffectSpan = document.querySelector("#gmaxEffect");

    hpForm.onchange = function(){
      let hpValue = hpForm.value;
      if(hpValue < 0 || isNaN(hpValue)) {
        hpForm.value = 0;
        return;
      }
      hpValue = Math.floor(hpValue)
      if(hpValue != hpForm.value){
        hpForm.value = hpValue;
      }
      let lowestValue = (value) => value != 0 ? Math.max(1, Math.floor(value)) : 0;

      // Handle Berries
      let berryRange = lowestValue(hpValue / 4);
      let berryRestore = lowestValue(hpValue / 3);
      let sitrusRange = lowestValue(hpValue / 2);
      let sitrusRestore = lowestValue(hpValue / 4);
      let effectBerryRange = lowestValue(hpValue / 2);
      berryRangeSpan.innerHTML = berryRange;
      berryRestoreSpan.innerHTML = berryRestore;
      sitrusRangeSpan.innerHTML = sitrusRange;
      sitrusRestoreSpan.innerHTML = sitrusRestore;
      effectBerrySpan.innerHTML = effectBerryRange;

      // Handle Items
      let lifeOrbDamage = lowestValue(hpValue / 10);
      let leftoversRestore = lowestValue(hpValue / 16);
      let blackSludgeDamage = lowestValue(hpValue / 8);
      let blackSludgeRestore = lowestValue(hpValue / 16);
      let stickyBarbDamage = lowestValue(hpValue / 8);
      lifeOrbSpan.innerHTML = lifeOrbDamage;
      leftoversSpan.innerHTML = leftoversRestore;
      blackSludgeDamageSpan.innerHTML = blackSludgeDamage;
      blackSludgeRestoreSpan.innerHTML = blackSludgeRestore;
      stickyBarbSpan.innerHTML = stickyBarbDamage;

      // Handle Weather and Poison
      let weatherDamage = lowestValue(hpValue / 16);
      let poisonDamage = lowestValue(hpValue / 8);
      weatherSpan.innerHTML = weatherDamage;
      poisonSpan.innerHTML = poisonDamage;

      // Handle Abilities
      let solarPowerDamage = lowestValue(hpValue / 8);
      let rainDishRestore = lowestValue(hpValue / 16);
      let iceBodyRestore = lowestValue(hpValue / 16);
      let drySkin = lowestValue(hpValue / 8);
      let absorbRestore = lowestValue(hpValue / 4);
      let regeneratorRestore = lowestValue(hpValue / 3);
      let poisonHealRestore = lowestValue(hpValue / 8);
      let badDreamsDamage = lowestValue(hpValue / 8);
      let gluttonyRange = lowestValue(hpValue / 2);
      let cheekPouchRange = lowestValue(hpValue / 3);
      let belowHalfRange = lowestValue(hpValue / 2);
      solarPowerSpan.innerHTML = solarPowerDamage;
      rainDishSpan.innerHTML = rainDishRestore;
      iceBodySpan.innerHTML = iceBodyRestore;
      drySkinDamageSpan.innerHTML = drySkin;
      drySkinRestoreSpan.innerHTML = drySkin;
      absorbSpan.innerHTML = absorbRestore;
      regeneratorSpan.innerHTML = regeneratorRestore;
      poisonHealSpan.innerHTML = poisonHealRestore;
      badDreamsSpan.innerHTML = badDreamsDamage;
      gluttonySpan.innerHTML = gluttonyRange;
      cheekPouchSpan.innerHTML = cheekPouchRange;
      belowHalf.innerHTML = belowHalfRange;

      // Handle Move Effects
      let bindingDamage = lowestValue(hpValue / 8);
      let gmaxEffectDamage = lowestValue(hpValue / 6);
      bindingSpan.innerHTML = bindingDamage;
      gmaxEffectSpan.innerHTML = gmaxEffectDamage;
    };
  };
</script>
