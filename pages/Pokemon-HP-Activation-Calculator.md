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
Sitrus Berry would activate at <span id="sitrusRange">0</span> HP and heal <span id="sitrusRestore">0</span> HP.<br/>
Figy Berry, Wiki Berry, Mago Berry, Aguav Berry, and Iapapa Berry would activate at <span id="berryRange">0</span> HP and heal <span id="berryRestore">0</span> HP.<br/>
Liechi Berry, Ganlon Berry, Salac Berry, Petaya Berry, Apicot Berry, Lansat Berry, Starf Berry, Micle Berry, or Custap Berry would activate at <span id="effectBerry">0</span> HP and get its effect.<br/>

<p class="title">Items:</p>
Life Orb would deal <span id="lifeOrb">0</span> damage on attacks.<br/>
Leftovers would heal <span id="leftovers">0</span> HP at the end of the turn.<br/>
Black Sludge would deal <span id="blackSludgeDamage">0</span> damage to non-Poison Pokémon at the end of the turn and heal <span id="blackSludgeRestore">0</span> HP to Poison Pokémon.<br/>
Sticky Barb would deal <span id="stickyBarb">0</span> damage at the end of the turn.<br/>

<p class="title">Weather and Status:</p>
Hail and Sandstorm would deal <span id="weather">0</span> damage at the end of the turn.<br/>
Poison would deal <span id="poison">0</span> damage at the end of the turn.<br/>

<p class="title">Abilities:</p>
Solar Power would deal <span id="solarPower">0</span> damage in sun at the end of the turn.<br/>
Rain Dish and Ice Body would heal <span id="weatherHeal">0</span> HP in rain or hail repsectively at the end of the turn.<br/>
Dry Skin would deal <span id="drySkinDamage">0</span> damage in sun at the end of the turn and heal <span id="drySkinRestore">0</span> HP in rain at the end of the turn.<br/>
Volt Absorb and Water Absorb would heal <span id="absorb">0</span> HP when hit by a Water or Electric move respectively.<br/>
Regenerator would heal <span id="regenerator">0</span> d on switch out.<br/>
Poison Heal would heal <span id="poisonHeal">0</span> HP at the end of the turn.<br/>
Bad Dreams would deal <span id="badDreams">0</span> damage to sleeping Pokémon at the end of the turn.<br/>
Gluttony would activate at <span id="gluttony">0</span> HP and consume a berry.<br/>
Cheek Pouch would heal <span id="cheekPouch">0</span> HP after consuming a berry.<br/>
Zen Mode, Wimp Out, Emergency Exit, Shields Down and Schooling, and Beserk would activate below <span id="belowHalf">0</span> HP.<br/>

<p class="title">Move Effects:</p>
Substitute would require <span id="substitute">0</span> HP to activate.<br/>
Bind, Clamp, Fire Spin, Infestation, Magma Storm, Sand Tomb, Snap Trap, Thunder Cage, Whirlpool, Wrap, G-Max Centiferno, and G-Max Sandblast would deal <span id="binding">0</span> damage at the end of the turn.<br/>
G-Max Wildfire, G-Max Cannonade, and G-Max Vine Lash would deal <span id="gmaxEffect"></span> damage at the end of the turn.
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
    const weatherHealSpan = document.querySelector("#weatherHeal");
    const drySkinDamageSpan = document.querySelector("#drySkinDamage");
    const drySkinRestoreSpan = document.querySelector("#drySkinRestore");
    const absorbSpan = document.querySelector("#absorb");
    const regeneratorSpan = document.querySelector("#regenerator");
    const poisonHealSpan = document.querySelector("#poisonHeal");
    const badDreamsSpan = document.querySelector("#badDreams");
    const gluttonySpan = document.querySelector("#gluttony");
    const cheekPouchSpan = document.querySelector("#cheekPouch");
    const belowHalfSpan = document.querySelector("#belowHalf");
    const substituteSpan = document.querySelector("#substitute");
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

      // Do common calcs ahead of time since there are many repeated ones.
      let halfValue = lowestValue(hpValue / 2);
      let thirdValue = lowestValue(hpValue / 3);
      let quarterValue = lowestValue(hpValue / 4);
      let eightValue = lowestValue(hpValue / 8);
      let sixteenthValue = lowestValue(hpValue / 16);

      // Handle Berries
      berryRangeSpan.innerHTML = quarterValue;
      berryRestoreSpan.innerHTML = thirdValue;
      sitrusRangeSpan.innerHTML = halfValue;
      sitrusRestoreSpan.innerHTML = quarterValue;
      effectBerrySpan.innerHTML = halfValue;

      // Handle Items
      lifeOrbSpan.innerHTML = lowestValue(hpValue / 10);
      leftoversSpan.innerHTML = sixteenthValue;
      blackSludgeDamageSpan.innerHTML = eightValue;
      blackSludgeRestoreSpan.innerHTML = sixteenthValue;
      stickyBarbSpan.innerHTML = eightValue;

      // Handle Weather and Poison
      weatherSpan.innerHTML = sixteenthValue;
      poisonSpan.innerHTML = eightValue;

      // Handle Abilities
      solarPowerSpan.innerHTML =  eightValue;
      weatherHealSpan.innerHTML = sixteenthValue;
      drySkinDamageSpan.innerHTML = eightValue;
      drySkinRestoreSpan.innerHTML = eightValue;
      absorbSpan.innerHTML = quarterValue;
      regeneratorSpan.innerHTML = thirdValue;
      poisonHealSpan.innerHTML = eightValue;
      badDreamsSpan.innerHTML = eightValue;
      gluttonySpan.innerHTML = halfValue;
      cheekPouchSpan.innerHTML = thirdValue;
      belowHalf.innerHTML = halfValue;

      // Handle Move Effects
      substituteSpan.innerHTML = quarterValue;
      bindingSpan.innerHTML = eightValue;
      gmaxEffectSpan.innerHTML = lowestValue(hpValue / 6);
    };
  };
</script>
