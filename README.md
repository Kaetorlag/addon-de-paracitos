# Addon de Parásitos Evolutivos (Bedrock)

Addon completo inspirado en un sistema de parásitos evolutivos, con **Behavior Pack + Resource Pack**. Incluye 7 fases de evolución, armas, armaduras, loot progresivo, partículas, sonidos y una propuesta de encantamientos personalizados compatible con Bedrock sin scripts experimentales.

> **Nota importante:** Este repositorio **no incluye archivos binarios** (texturas `.png` ni sonidos `.ogg`). Debes añadirlos manualmente en el Resource Pack siguiendo las rutas indicadas abajo.

## ✅ Contenido principal

### Entidades parásitas (7 niveles)
Cada nivel es más peligroso que el anterior y cuenta con:
- **Modelo y textura propios** (7 geometrías + rutas de texturas definidas).
- Escalado de vida, daño, velocidad y IA.
- Evolución por muertes (evento `minecraft:on_kill_entity`) y por tiempo (`minecraft:timer`).

**Resumen de fases:**
1. Pequeño y débil, aparece de noche, infecta mobs pasivos.
2. Más rápido y resistente, prioriza aldeanos.
3. Ataque ácido, rompe bloques blandos.
4. Puede invocar parásitos menores.
5. Resistente a armas básicas, detecta jugadores a larga distancia.
6. Mutación gigante con salto y embestida.
7. Jefe con múltiples fases y drop exclusivo.

### Parásitos infectores por mob (7 niveles)
Se añadieron variantes parásitas por tipo de mob (cada una con 7 niveles):
- Vaca, Cerdo, Oveja, Gallina
- Bacalao, Burro, Caballo, Caballo esqueleto, Camello
- Calamar, Calamar luminoso, Conejo, Gato, Zorro, Ocelote
- Champivaca y Champivaca marrón
- Mula, Murciélago, Loro, Vendedor ambulante
- Pez tropical, Pez globo, Salmón, Rana, Renacuajo, Tortuga
- Esnifel, Gólem de nieve, Vagante
- Abeja, Cabra, Delfín, Gólem de hierro, Llama, Lobo
- Oso polar, Panda, Piglin, Piglin bruto, Zoglin, Hoglin
- Ajolote, Allay, Armadillo
- Ender Dragon, Endermite, Shulker, Slime, Vex
- Ahogado, Zombi aldeano, Zombi desértico, Esqueleto wither
- Esqueleto glacial, Araña de cueva, Blaze, Brisa, Ghast
- Guardián, Guardián anciano, Evocador, Vindicator, Saqueador
- Enderman, Araña, Bruja, Creeper, Zombi, Esqueleto, Wither
- Jinete avícola y Devastador

> Identificadores: `addon:parasite_<mob>_lvl1..lvl7` (ej: `addon:parasite_cow_lvl4`).

### Flor parasitaria (nido)
Se añade una entidad **Flor parasitaria** (`addon:parasite_bloom`) que genera parásitos de nivel 1 de forma periódica. Puede usarse como nido o fuente de infección ambiental.

### Flores parasitarias por nivel (1–7)
Se añaden 7 flores (`addon:parasite_bloom_lvl1..lvl7`). Cada nivel puede invocar:
- Parásitos base del mismo nivel (`addon:parasite_lvlN`).
- Parásitos infectores por mob del mismo nivel.

### Fases mundiales por días (1–7)
Se añadieron controladores de fase mundial (`addon:world_phase_controller_lvl1..lvl7`) que evolucionan automáticamente **cada 10 días** (240000 ticks). No reemplaza los spawns vanilla, pero sirve como “estado global” para comandos o sistemas externos:
- Fase 1: días 1–10
- Fase 2: días 10–20
- ...
- Fase 7: días 60–70

Para activar el sistema: `/summon addon:world_phase_controller_lvl1`.

### Evolución
Las entidades usan:
- `component_groups` + `events` para transformación.
- `minecraft:timer` para evolución automática.
- `minecraft:on_kill_entity` para evolución por combate.

### Armas especiales
- **Espada antibiótica**: daño extra vs parásitos.
- **Arco corrosivo**: proyectil con veneno.
- **Lanza biológica**: daño alto y penetrante.
- **25 armas radioactivas** (`radio_weapon_01..25`).

### Armaduras
Set completo anti-parásitos con:
- Reducción de daño biológico.
- Resistencia a infección.
- Bonus de set (propuesto vía tags para eventos).
- **25 armaduras radioactivas** (`radio_armor_01..25`).

### Encantamientos personalizados (sistema por tags)
Se implementa un sistema de “encantamientos” usando **tags, eventos y sensores de daño**:
- **Purificación (I–V)**
- **Antibiótico (I–III)**
- **Disrupción Celular (I–II)**
- **Exterminio (único)**
- **Inmunidad (I–IV)**
- **Bioblindaje (I–III)**
- **Regeneración Sintética (I–II)**
- **25 encantamientos radioactivos** (`book_radio_01..25`) crafteables con **1 lingote de radio + 1 libro**.

> Los libros encantados son ítems dedicados (`addon:book_*`) que otorgan tags usados por los parásitos para activar eventos.

### Mineral radio
Se añade un mineral **Radio** (verde brillante y más raro que el diamante). Incluye:
- `addon:radio_ore`
- `addon:radio_ingot`

### Drops y loot
- Biomasa parasitaria base.
- Núcleo mutágeno desde nivel 3.
- Libros encantados raros desde nivel 5.
- Reliquia del jefe + Exterminio en nivel 7.

### Sonidos y partículas
Incluye definiciones listas para usar:
- `addon.parasite.attack`
- `addon.parasite.death`
- `addon.parasite.evolve`

## 📦 Estructura del addon

```
behavior_pack/
  manifest.json
  entities/
  items/
  loot_tables/
  recipes/
  spawn_rules/
resource_pack/
  manifest.json
  entity/
  models/
  textures/
  particles/
  sounds/
  texts/
```

## 🎨 Archivos binarios a añadir manualmente

Crea los archivos de texturas y sonidos en estas rutas:

**Texturas (PNG)**
```
resource_pack/textures/entity/parasite_lvl1.png
resource_pack/textures/entity/parasite_lvl2.png
resource_pack/textures/entity/parasite_lvl3.png
resource_pack/textures/entity/parasite_lvl4.png
resource_pack/textures/entity/parasite_lvl5.png
resource_pack/textures/entity/parasite_lvl6.png
resource_pack/textures/entity/parasite_lvl7.png
resource_pack/textures/entity/parasite_bloom.png
resource_pack/textures/entity/parasite_bloom_lvl1.png
resource_pack/textures/entity/parasite_bloom_lvl2.png
resource_pack/textures/entity/parasite_bloom_lvl3.png
resource_pack/textures/entity/parasite_bloom_lvl4.png
resource_pack/textures/entity/parasite_bloom_lvl5.png
resource_pack/textures/entity/parasite_bloom_lvl6.png
resource_pack/textures/entity/parasite_bloom_lvl7.png
resource_pack/textures/entity/parasite_cow_lvl1.png
resource_pack/textures/entity/parasite_cow_lvl2.png
resource_pack/textures/entity/parasite_cow_lvl3.png
resource_pack/textures/entity/parasite_cow_lvl4.png
resource_pack/textures/entity/parasite_cow_lvl5.png
resource_pack/textures/entity/parasite_cow_lvl6.png
resource_pack/textures/entity/parasite_cow_lvl7.png
resource_pack/textures/entity/parasite_pig_lvl1.png
resource_pack/textures/entity/parasite_pig_lvl2.png
resource_pack/textures/entity/parasite_pig_lvl3.png
resource_pack/textures/entity/parasite_pig_lvl4.png
resource_pack/textures/entity/parasite_pig_lvl5.png
resource_pack/textures/entity/parasite_pig_lvl6.png
resource_pack/textures/entity/parasite_pig_lvl7.png
resource_pack/textures/entity/parasite_sheep_lvl1.png
resource_pack/textures/entity/parasite_sheep_lvl2.png
resource_pack/textures/entity/parasite_sheep_lvl3.png
resource_pack/textures/entity/parasite_sheep_lvl4.png
resource_pack/textures/entity/parasite_sheep_lvl5.png
resource_pack/textures/entity/parasite_sheep_lvl6.png
resource_pack/textures/entity/parasite_sheep_lvl7.png
resource_pack/textures/entity/parasite_chicken_lvl1.png
resource_pack/textures/entity/parasite_chicken_lvl2.png
resource_pack/textures/entity/parasite_chicken_lvl3.png
resource_pack/textures/entity/parasite_chicken_lvl4.png
resource_pack/textures/entity/parasite_chicken_lvl5.png
resource_pack/textures/entity/parasite_chicken_lvl6.png
resource_pack/textures/entity/parasite_chicken_lvl7.png
resource_pack/textures/entity/parasite_villager_lvl1.png
resource_pack/textures/entity/parasite_villager_lvl2.png
resource_pack/textures/entity/parasite_villager_lvl3.png
resource_pack/textures/entity/parasite_villager_lvl4.png
resource_pack/textures/entity/parasite_villager_lvl5.png
resource_pack/textures/entity/parasite_villager_lvl6.png
resource_pack/textures/entity/parasite_villager_lvl7.png
resource_pack/textures/entity/parasite_zombie_lvl1.png
resource_pack/textures/entity/parasite_zombie_lvl2.png
resource_pack/textures/entity/parasite_zombie_lvl3.png
resource_pack/textures/entity/parasite_zombie_lvl4.png
resource_pack/textures/entity/parasite_zombie_lvl5.png
resource_pack/textures/entity/parasite_zombie_lvl6.png
resource_pack/textures/entity/parasite_zombie_lvl7.png
resource_pack/textures/entity/parasite_skeleton_lvl1.png
resource_pack/textures/entity/parasite_skeleton_lvl2.png
resource_pack/textures/entity/parasite_skeleton_lvl3.png
resource_pack/textures/entity/parasite_skeleton_lvl4.png
resource_pack/textures/entity/parasite_skeleton_lvl5.png
resource_pack/textures/entity/parasite_skeleton_lvl6.png
resource_pack/textures/entity/parasite_skeleton_lvl7.png
resource_pack/textures/entity/parasite_creeper_lvl1.png
resource_pack/textures/entity/parasite_creeper_lvl2.png
resource_pack/textures/entity/parasite_creeper_lvl3.png
resource_pack/textures/entity/parasite_creeper_lvl4.png
resource_pack/textures/entity/parasite_creeper_lvl5.png
resource_pack/textures/entity/parasite_creeper_lvl6.png
resource_pack/textures/entity/parasite_creeper_lvl7.png
resource_pack/textures/entity/parasite_enderman_lvl1.png
resource_pack/textures/entity/parasite_enderman_lvl2.png
resource_pack/textures/entity/parasite_enderman_lvl3.png
resource_pack/textures/entity/parasite_enderman_lvl4.png
resource_pack/textures/entity/parasite_enderman_lvl5.png
resource_pack/textures/entity/parasite_enderman_lvl6.png
resource_pack/textures/entity/parasite_enderman_lvl7.png
resource_pack/textures/entity/parasite_spider_lvl1.png
resource_pack/textures/entity/parasite_spider_lvl2.png
resource_pack/textures/entity/parasite_spider_lvl3.png
resource_pack/textures/entity/parasite_spider_lvl4.png
resource_pack/textures/entity/parasite_spider_lvl5.png
resource_pack/textures/entity/parasite_spider_lvl6.png
resource_pack/textures/entity/parasite_spider_lvl7.png
resource_pack/textures/entity/parasite_witch_lvl1.png
resource_pack/textures/entity/parasite_witch_lvl2.png
resource_pack/textures/entity/parasite_witch_lvl3.png
resource_pack/textures/entity/parasite_witch_lvl4.png
resource_pack/textures/entity/parasite_witch_lvl5.png
resource_pack/textures/entity/parasite_witch_lvl6.png
resource_pack/textures/entity/parasite_witch_lvl7.png
resource_pack/textures/entity/parasite_warden_lvl1.png
resource_pack/textures/entity/parasite_warden_lvl2.png
resource_pack/textures/entity/parasite_warden_lvl3.png
resource_pack/textures/entity/parasite_warden_lvl4.png
resource_pack/textures/entity/parasite_warden_lvl5.png
resource_pack/textures/entity/parasite_warden_lvl6.png
resource_pack/textures/entity/parasite_warden_lvl7.png
resource_pack/textures/entity/parasite_wither_lvl1.png
resource_pack/textures/entity/parasite_wither_lvl2.png
resource_pack/textures/entity/parasite_wither_lvl3.png
resource_pack/textures/entity/parasite_wither_lvl4.png
resource_pack/textures/entity/parasite_wither_lvl5.png
resource_pack/textures/entity/parasite_wither_lvl6.png
resource_pack/textures/entity/parasite_wither_lvl7.png
resource_pack/textures/entity/parasite_cod_lvl1.png
resource_pack/textures/entity/parasite_cod_lvl2.png
resource_pack/textures/entity/parasite_cod_lvl3.png
resource_pack/textures/entity/parasite_cod_lvl4.png
resource_pack/textures/entity/parasite_cod_lvl5.png
resource_pack/textures/entity/parasite_cod_lvl6.png
resource_pack/textures/entity/parasite_cod_lvl7.png
resource_pack/textures/entity/parasite_donkey_lvl1.png
resource_pack/textures/entity/parasite_donkey_lvl2.png
resource_pack/textures/entity/parasite_donkey_lvl3.png
resource_pack/textures/entity/parasite_donkey_lvl4.png
resource_pack/textures/entity/parasite_donkey_lvl5.png
resource_pack/textures/entity/parasite_donkey_lvl6.png
resource_pack/textures/entity/parasite_donkey_lvl7.png
resource_pack/textures/entity/parasite_horse_lvl1.png
resource_pack/textures/entity/parasite_horse_lvl2.png
resource_pack/textures/entity/parasite_horse_lvl3.png
resource_pack/textures/entity/parasite_horse_lvl4.png
resource_pack/textures/entity/parasite_horse_lvl5.png
resource_pack/textures/entity/parasite_horse_lvl6.png
resource_pack/textures/entity/parasite_horse_lvl7.png
resource_pack/textures/entity/parasite_skeleton_horse_lvl1.png
resource_pack/textures/entity/parasite_skeleton_horse_lvl2.png
resource_pack/textures/entity/parasite_skeleton_horse_lvl3.png
resource_pack/textures/entity/parasite_skeleton_horse_lvl4.png
resource_pack/textures/entity/parasite_skeleton_horse_lvl5.png
resource_pack/textures/entity/parasite_skeleton_horse_lvl6.png
resource_pack/textures/entity/parasite_skeleton_horse_lvl7.png
resource_pack/textures/entity/parasite_squid_lvl1.png
resource_pack/textures/entity/parasite_squid_lvl2.png
resource_pack/textures/entity/parasite_squid_lvl3.png
resource_pack/textures/entity/parasite_squid_lvl4.png
resource_pack/textures/entity/parasite_squid_lvl5.png
resource_pack/textures/entity/parasite_squid_lvl6.png
resource_pack/textures/entity/parasite_squid_lvl7.png
resource_pack/textures/entity/parasite_glow_squid_lvl1.png
resource_pack/textures/entity/parasite_glow_squid_lvl2.png
resource_pack/textures/entity/parasite_glow_squid_lvl3.png
resource_pack/textures/entity/parasite_glow_squid_lvl4.png
resource_pack/textures/entity/parasite_glow_squid_lvl5.png
resource_pack/textures/entity/parasite_glow_squid_lvl6.png
resource_pack/textures/entity/parasite_glow_squid_lvl7.png
resource_pack/textures/entity/parasite_camel_lvl1.png
resource_pack/textures/entity/parasite_camel_lvl2.png
resource_pack/textures/entity/parasite_camel_lvl3.png
resource_pack/textures/entity/parasite_camel_lvl4.png
resource_pack/textures/entity/parasite_camel_lvl5.png
resource_pack/textures/entity/parasite_camel_lvl6.png
resource_pack/textures/entity/parasite_camel_lvl7.png
resource_pack/textures/entity/parasite_mooshroom_lvl1.png
resource_pack/textures/entity/parasite_mooshroom_lvl2.png
resource_pack/textures/entity/parasite_mooshroom_lvl3.png
resource_pack/textures/entity/parasite_mooshroom_lvl4.png
resource_pack/textures/entity/parasite_mooshroom_lvl5.png
resource_pack/textures/entity/parasite_mooshroom_lvl6.png
resource_pack/textures/entity/parasite_mooshroom_lvl7.png
resource_pack/textures/entity/parasite_mooshroom_brown_lvl1.png
resource_pack/textures/entity/parasite_mooshroom_brown_lvl2.png
resource_pack/textures/entity/parasite_mooshroom_brown_lvl3.png
resource_pack/textures/entity/parasite_mooshroom_brown_lvl4.png
resource_pack/textures/entity/parasite_mooshroom_brown_lvl5.png
resource_pack/textures/entity/parasite_mooshroom_brown_lvl6.png
resource_pack/textures/entity/parasite_mooshroom_brown_lvl7.png
resource_pack/textures/entity/parasite_rabbit_lvl1.png
resource_pack/textures/entity/parasite_rabbit_lvl2.png
resource_pack/textures/entity/parasite_rabbit_lvl3.png
resource_pack/textures/entity/parasite_rabbit_lvl4.png
resource_pack/textures/entity/parasite_rabbit_lvl5.png
resource_pack/textures/entity/parasite_rabbit_lvl6.png
resource_pack/textures/entity/parasite_rabbit_lvl7.png
resource_pack/textures/entity/parasite_cat_lvl1.png
resource_pack/textures/entity/parasite_cat_lvl2.png
resource_pack/textures/entity/parasite_cat_lvl3.png
resource_pack/textures/entity/parasite_cat_lvl4.png
resource_pack/textures/entity/parasite_cat_lvl5.png
resource_pack/textures/entity/parasite_cat_lvl6.png
resource_pack/textures/entity/parasite_cat_lvl7.png
resource_pack/textures/entity/parasite_snow_golem_lvl1.png
resource_pack/textures/entity/parasite_snow_golem_lvl2.png
resource_pack/textures/entity/parasite_snow_golem_lvl3.png
resource_pack/textures/entity/parasite_snow_golem_lvl4.png
resource_pack/textures/entity/parasite_snow_golem_lvl5.png
resource_pack/textures/entity/parasite_snow_golem_lvl6.png
resource_pack/textures/entity/parasite_snow_golem_lvl7.png
resource_pack/textures/entity/parasite_stray_lvl1.png
resource_pack/textures/entity/parasite_stray_lvl2.png
resource_pack/textures/entity/parasite_stray_lvl3.png
resource_pack/textures/entity/parasite_stray_lvl4.png
resource_pack/textures/entity/parasite_stray_lvl5.png
resource_pack/textures/entity/parasite_stray_lvl6.png
resource_pack/textures/entity/parasite_stray_lvl7.png
resource_pack/textures/entity/parasite_parrot_lvl1.png
resource_pack/textures/entity/parasite_parrot_lvl2.png
resource_pack/textures/entity/parasite_parrot_lvl3.png
resource_pack/textures/entity/parasite_parrot_lvl4.png
resource_pack/textures/entity/parasite_parrot_lvl5.png
resource_pack/textures/entity/parasite_parrot_lvl6.png
resource_pack/textures/entity/parasite_parrot_lvl7.png
resource_pack/textures/entity/parasite_mule_lvl1.png
resource_pack/textures/entity/parasite_mule_lvl2.png
resource_pack/textures/entity/parasite_mule_lvl3.png
resource_pack/textures/entity/parasite_mule_lvl4.png
resource_pack/textures/entity/parasite_mule_lvl5.png
resource_pack/textures/entity/parasite_mule_lvl6.png
resource_pack/textures/entity/parasite_mule_lvl7.png
resource_pack/textures/entity/parasite_bat_lvl1.png
resource_pack/textures/entity/parasite_bat_lvl2.png
resource_pack/textures/entity/parasite_bat_lvl3.png
resource_pack/textures/entity/parasite_bat_lvl4.png
resource_pack/textures/entity/parasite_bat_lvl5.png
resource_pack/textures/entity/parasite_bat_lvl6.png
resource_pack/textures/entity/parasite_bat_lvl7.png
resource_pack/textures/entity/parasite_ocelot_lvl1.png
resource_pack/textures/entity/parasite_ocelot_lvl2.png
resource_pack/textures/entity/parasite_ocelot_lvl3.png
resource_pack/textures/entity/parasite_ocelot_lvl4.png
resource_pack/textures/entity/parasite_ocelot_lvl5.png
resource_pack/textures/entity/parasite_ocelot_lvl6.png
resource_pack/textures/entity/parasite_ocelot_lvl7.png
resource_pack/textures/entity/parasite_tropical_fish_lvl1.png
resource_pack/textures/entity/parasite_tropical_fish_lvl2.png
resource_pack/textures/entity/parasite_tropical_fish_lvl3.png
resource_pack/textures/entity/parasite_tropical_fish_lvl4.png
resource_pack/textures/entity/parasite_tropical_fish_lvl5.png
resource_pack/textures/entity/parasite_tropical_fish_lvl6.png
resource_pack/textures/entity/parasite_tropical_fish_lvl7.png
resource_pack/textures/entity/parasite_pufferfish_lvl1.png
resource_pack/textures/entity/parasite_pufferfish_lvl2.png
resource_pack/textures/entity/parasite_pufferfish_lvl3.png
resource_pack/textures/entity/parasite_pufferfish_lvl4.png
resource_pack/textures/entity/parasite_pufferfish_lvl5.png
resource_pack/textures/entity/parasite_pufferfish_lvl6.png
resource_pack/textures/entity/parasite_pufferfish_lvl7.png
resource_pack/textures/entity/parasite_frog_lvl1.png
resource_pack/textures/entity/parasite_frog_lvl2.png
resource_pack/textures/entity/parasite_frog_lvl3.png
resource_pack/textures/entity/parasite_frog_lvl4.png
resource_pack/textures/entity/parasite_frog_lvl5.png
resource_pack/textures/entity/parasite_frog_lvl6.png
resource_pack/textures/entity/parasite_frog_lvl7.png
resource_pack/textures/entity/parasite_tadpole_lvl1.png
resource_pack/textures/entity/parasite_tadpole_lvl2.png
resource_pack/textures/entity/parasite_tadpole_lvl3.png
resource_pack/textures/entity/parasite_tadpole_lvl4.png
resource_pack/textures/entity/parasite_tadpole_lvl5.png
resource_pack/textures/entity/parasite_tadpole_lvl6.png
resource_pack/textures/entity/parasite_tadpole_lvl7.png
resource_pack/textures/entity/parasite_salmon_lvl1.png
resource_pack/textures/entity/parasite_salmon_lvl2.png
resource_pack/textures/entity/parasite_salmon_lvl3.png
resource_pack/textures/entity/parasite_salmon_lvl4.png
resource_pack/textures/entity/parasite_salmon_lvl5.png
resource_pack/textures/entity/parasite_salmon_lvl6.png
resource_pack/textures/entity/parasite_salmon_lvl7.png
resource_pack/textures/entity/parasite_sniffer_lvl1.png
resource_pack/textures/entity/parasite_sniffer_lvl2.png
resource_pack/textures/entity/parasite_sniffer_lvl3.png
resource_pack/textures/entity/parasite_sniffer_lvl4.png
resource_pack/textures/entity/parasite_sniffer_lvl5.png
resource_pack/textures/entity/parasite_sniffer_lvl6.png
resource_pack/textures/entity/parasite_sniffer_lvl7.png
resource_pack/textures/entity/parasite_turtle_lvl1.png
resource_pack/textures/entity/parasite_turtle_lvl2.png
resource_pack/textures/entity/parasite_turtle_lvl3.png
resource_pack/textures/entity/parasite_turtle_lvl4.png
resource_pack/textures/entity/parasite_turtle_lvl5.png
resource_pack/textures/entity/parasite_turtle_lvl6.png
resource_pack/textures/entity/parasite_turtle_lvl7.png
resource_pack/textures/entity/parasite_wandering_trader_lvl1.png
resource_pack/textures/entity/parasite_wandering_trader_lvl2.png
resource_pack/textures/entity/parasite_wandering_trader_lvl3.png
resource_pack/textures/entity/parasite_wandering_trader_lvl4.png
resource_pack/textures/entity/parasite_wandering_trader_lvl5.png
resource_pack/textures/entity/parasite_wandering_trader_lvl6.png
resource_pack/textures/entity/parasite_wandering_trader_lvl7.png
resource_pack/textures/entity/parasite_fox_lvl1.png
resource_pack/textures/entity/parasite_fox_lvl2.png
resource_pack/textures/entity/parasite_fox_lvl3.png
resource_pack/textures/entity/parasite_fox_lvl4.png
resource_pack/textures/entity/parasite_fox_lvl5.png
resource_pack/textures/entity/parasite_fox_lvl6.png
resource_pack/textures/entity/parasite_fox_lvl7.png
resource_pack/textures/entity/parasite_bee_lvl1.png
resource_pack/textures/entity/parasite_bee_lvl2.png
resource_pack/textures/entity/parasite_bee_lvl3.png
resource_pack/textures/entity/parasite_bee_lvl4.png
resource_pack/textures/entity/parasite_bee_lvl5.png
resource_pack/textures/entity/parasite_bee_lvl6.png
resource_pack/textures/entity/parasite_bee_lvl7.png
resource_pack/textures/entity/parasite_cave_spider_lvl1.png
resource_pack/textures/entity/parasite_cave_spider_lvl2.png
resource_pack/textures/entity/parasite_cave_spider_lvl3.png
resource_pack/textures/entity/parasite_cave_spider_lvl4.png
resource_pack/textures/entity/parasite_cave_spider_lvl5.png
resource_pack/textures/entity/parasite_cave_spider_lvl6.png
resource_pack/textures/entity/parasite_cave_spider_lvl7.png
resource_pack/textures/entity/parasite_goat_lvl1.png
resource_pack/textures/entity/parasite_goat_lvl2.png
resource_pack/textures/entity/parasite_goat_lvl3.png
resource_pack/textures/entity/parasite_goat_lvl4.png
resource_pack/textures/entity/parasite_goat_lvl5.png
resource_pack/textures/entity/parasite_goat_lvl6.png
resource_pack/textures/entity/parasite_goat_lvl7.png
resource_pack/textures/entity/parasite_dolphin_lvl1.png
resource_pack/textures/entity/parasite_dolphin_lvl2.png
resource_pack/textures/entity/parasite_dolphin_lvl3.png
resource_pack/textures/entity/parasite_dolphin_lvl4.png
resource_pack/textures/entity/parasite_dolphin_lvl5.png
resource_pack/textures/entity/parasite_dolphin_lvl6.png
resource_pack/textures/entity/parasite_dolphin_lvl7.png
resource_pack/textures/entity/parasite_iron_golem_lvl1.png
resource_pack/textures/entity/parasite_iron_golem_lvl2.png
resource_pack/textures/entity/parasite_iron_golem_lvl3.png
resource_pack/textures/entity/parasite_iron_golem_lvl4.png
resource_pack/textures/entity/parasite_iron_golem_lvl5.png
resource_pack/textures/entity/parasite_iron_golem_lvl6.png
resource_pack/textures/entity/parasite_iron_golem_lvl7.png
resource_pack/textures/entity/parasite_llama_lvl1.png
resource_pack/textures/entity/parasite_llama_lvl2.png
resource_pack/textures/entity/parasite_llama_lvl3.png
resource_pack/textures/entity/parasite_llama_lvl4.png
resource_pack/textures/entity/parasite_llama_lvl5.png
resource_pack/textures/entity/parasite_llama_lvl6.png
resource_pack/textures/entity/parasite_llama_lvl7.png
resource_pack/textures/entity/parasite_wolf_lvl1.png
resource_pack/textures/entity/parasite_wolf_lvl2.png
resource_pack/textures/entity/parasite_wolf_lvl3.png
resource_pack/textures/entity/parasite_wolf_lvl4.png
resource_pack/textures/entity/parasite_wolf_lvl5.png
resource_pack/textures/entity/parasite_wolf_lvl6.png
resource_pack/textures/entity/parasite_wolf_lvl7.png
resource_pack/textures/entity/parasite_polar_bear_lvl1.png
resource_pack/textures/entity/parasite_polar_bear_lvl2.png
resource_pack/textures/entity/parasite_polar_bear_lvl3.png
resource_pack/textures/entity/parasite_polar_bear_lvl4.png
resource_pack/textures/entity/parasite_polar_bear_lvl5.png
resource_pack/textures/entity/parasite_polar_bear_lvl6.png
resource_pack/textures/entity/parasite_polar_bear_lvl7.png
resource_pack/textures/entity/parasite_panda_lvl1.png
resource_pack/textures/entity/parasite_panda_lvl2.png
resource_pack/textures/entity/parasite_panda_lvl3.png
resource_pack/textures/entity/parasite_panda_lvl4.png
resource_pack/textures/entity/parasite_panda_lvl5.png
resource_pack/textures/entity/parasite_panda_lvl6.png
resource_pack/textures/entity/parasite_panda_lvl7.png
resource_pack/textures/entity/parasite_piglin_lvl1.png
resource_pack/textures/entity/parasite_piglin_lvl2.png
resource_pack/textures/entity/parasite_piglin_lvl3.png
resource_pack/textures/entity/parasite_piglin_lvl4.png
resource_pack/textures/entity/parasite_piglin_lvl5.png
resource_pack/textures/entity/parasite_piglin_lvl6.png
resource_pack/textures/entity/parasite_piglin_lvl7.png
resource_pack/textures/entity/parasite_chicken_jockey_lvl1.png
resource_pack/textures/entity/parasite_chicken_jockey_lvl2.png
resource_pack/textures/entity/parasite_chicken_jockey_lvl3.png
resource_pack/textures/entity/parasite_chicken_jockey_lvl4.png
resource_pack/textures/entity/parasite_chicken_jockey_lvl5.png
resource_pack/textures/entity/parasite_chicken_jockey_lvl6.png
resource_pack/textures/entity/parasite_chicken_jockey_lvl7.png
resource_pack/textures/entity/parasite_ravager_lvl1.png
resource_pack/textures/entity/parasite_ravager_lvl2.png
resource_pack/textures/entity/parasite_ravager_lvl3.png
resource_pack/textures/entity/parasite_ravager_lvl4.png
resource_pack/textures/entity/parasite_ravager_lvl5.png
resource_pack/textures/entity/parasite_ravager_lvl6.png
resource_pack/textures/entity/parasite_ravager_lvl7.png
resource_pack/textures/entity/parasite_drowned_lvl1.png
resource_pack/textures/entity/parasite_drowned_lvl2.png
resource_pack/textures/entity/parasite_drowned_lvl3.png
resource_pack/textures/entity/parasite_drowned_lvl4.png
resource_pack/textures/entity/parasite_drowned_lvl5.png
resource_pack/textures/entity/parasite_drowned_lvl6.png
resource_pack/textures/entity/parasite_drowned_lvl7.png
resource_pack/textures/entity/parasite_zombie_villager_lvl1.png
resource_pack/textures/entity/parasite_zombie_villager_lvl2.png
resource_pack/textures/entity/parasite_zombie_villager_lvl3.png
resource_pack/textures/entity/parasite_zombie_villager_lvl4.png
resource_pack/textures/entity/parasite_zombie_villager_lvl5.png
resource_pack/textures/entity/parasite_zombie_villager_lvl6.png
resource_pack/textures/entity/parasite_zombie_villager_lvl7.png
resource_pack/textures/entity/parasite_blaze_lvl1.png
resource_pack/textures/entity/parasite_blaze_lvl2.png
resource_pack/textures/entity/parasite_blaze_lvl3.png
resource_pack/textures/entity/parasite_blaze_lvl4.png
resource_pack/textures/entity/parasite_blaze_lvl5.png
resource_pack/textures/entity/parasite_blaze_lvl6.png
resource_pack/textures/entity/parasite_blaze_lvl7.png
resource_pack/textures/entity/parasite_breeze_lvl1.png
resource_pack/textures/entity/parasite_breeze_lvl2.png
resource_pack/textures/entity/parasite_breeze_lvl3.png
resource_pack/textures/entity/parasite_breeze_lvl4.png
resource_pack/textures/entity/parasite_breeze_lvl5.png
resource_pack/textures/entity/parasite_breeze_lvl6.png
resource_pack/textures/entity/parasite_breeze_lvl7.png
resource_pack/textures/entity/parasite_magma_cube_lvl1.png
resource_pack/textures/entity/parasite_magma_cube_lvl2.png
resource_pack/textures/entity/parasite_magma_cube_lvl3.png
resource_pack/textures/entity/parasite_magma_cube_lvl4.png
resource_pack/textures/entity/parasite_magma_cube_lvl5.png
resource_pack/textures/entity/parasite_magma_cube_lvl6.png
resource_pack/textures/entity/parasite_magma_cube_lvl7.png
resource_pack/textures/entity/parasite_endermite_lvl1.png
resource_pack/textures/entity/parasite_endermite_lvl2.png
resource_pack/textures/entity/parasite_endermite_lvl3.png
resource_pack/textures/entity/parasite_endermite_lvl4.png
resource_pack/textures/entity/parasite_endermite_lvl5.png
resource_pack/textures/entity/parasite_endermite_lvl6.png
resource_pack/textures/entity/parasite_endermite_lvl7.png
resource_pack/textures/entity/parasite_husk_lvl1.png
resource_pack/textures/entity/parasite_husk_lvl2.png
resource_pack/textures/entity/parasite_husk_lvl3.png
resource_pack/textures/entity/parasite_husk_lvl4.png
resource_pack/textures/entity/parasite_husk_lvl5.png
resource_pack/textures/entity/parasite_husk_lvl6.png
resource_pack/textures/entity/parasite_husk_lvl7.png
resource_pack/textures/entity/parasite_wither_skeleton_lvl1.png
resource_pack/textures/entity/parasite_wither_skeleton_lvl2.png
resource_pack/textures/entity/parasite_wither_skeleton_lvl3.png
resource_pack/textures/entity/parasite_wither_skeleton_lvl4.png
resource_pack/textures/entity/parasite_wither_skeleton_lvl5.png
resource_pack/textures/entity/parasite_wither_skeleton_lvl6.png
resource_pack/textures/entity/parasite_wither_skeleton_lvl7.png
resource_pack/textures/entity/parasite_phantom_lvl1.png
resource_pack/textures/entity/parasite_phantom_lvl2.png
resource_pack/textures/entity/parasite_phantom_lvl3.png
resource_pack/textures/entity/parasite_phantom_lvl4.png
resource_pack/textures/entity/parasite_phantom_lvl5.png
resource_pack/textures/entity/parasite_phantom_lvl6.png
resource_pack/textures/entity/parasite_phantom_lvl7.png
resource_pack/textures/entity/parasite_ghast_lvl1.png
resource_pack/textures/entity/parasite_ghast_lvl2.png
resource_pack/textures/entity/parasite_ghast_lvl3.png
resource_pack/textures/entity/parasite_ghast_lvl4.png
resource_pack/textures/entity/parasite_ghast_lvl5.png
resource_pack/textures/entity/parasite_ghast_lvl6.png
resource_pack/textures/entity/parasite_ghast_lvl7.png
resource_pack/textures/entity/parasite_guardian_lvl1.png
resource_pack/textures/entity/parasite_guardian_lvl2.png
resource_pack/textures/entity/parasite_guardian_lvl3.png
resource_pack/textures/entity/parasite_guardian_lvl4.png
resource_pack/textures/entity/parasite_guardian_lvl5.png
resource_pack/textures/entity/parasite_guardian_lvl6.png
resource_pack/textures/entity/parasite_guardian_lvl7.png
resource_pack/textures/entity/parasite_elder_guardian_lvl1.png
resource_pack/textures/entity/parasite_elder_guardian_lvl2.png
resource_pack/textures/entity/parasite_elder_guardian_lvl3.png
resource_pack/textures/entity/parasite_elder_guardian_lvl4.png
resource_pack/textures/entity/parasite_elder_guardian_lvl5.png
resource_pack/textures/entity/parasite_elder_guardian_lvl6.png
resource_pack/textures/entity/parasite_elder_guardian_lvl7.png
resource_pack/textures/entity/parasite_hoglin_lvl1.png
resource_pack/textures/entity/parasite_hoglin_lvl2.png
resource_pack/textures/entity/parasite_hoglin_lvl3.png
resource_pack/textures/entity/parasite_hoglin_lvl4.png
resource_pack/textures/entity/parasite_hoglin_lvl5.png
resource_pack/textures/entity/parasite_hoglin_lvl6.png
resource_pack/textures/entity/parasite_hoglin_lvl7.png
resource_pack/textures/entity/parasite_evoker_lvl1.png
resource_pack/textures/entity/parasite_evoker_lvl2.png
resource_pack/textures/entity/parasite_evoker_lvl3.png
resource_pack/textures/entity/parasite_evoker_lvl4.png
resource_pack/textures/entity/parasite_evoker_lvl5.png
resource_pack/textures/entity/parasite_evoker_lvl6.png
resource_pack/textures/entity/parasite_evoker_lvl7.png
resource_pack/textures/entity/parasite_silverfish_lvl1.png
resource_pack/textures/entity/parasite_silverfish_lvl2.png
resource_pack/textures/entity/parasite_silverfish_lvl3.png
resource_pack/textures/entity/parasite_silverfish_lvl4.png
resource_pack/textures/entity/parasite_silverfish_lvl5.png
resource_pack/textures/entity/parasite_silverfish_lvl6.png
resource_pack/textures/entity/parasite_silverfish_lvl7.png
resource_pack/textures/entity/parasite_piglin_brute_lvl1.png
resource_pack/textures/entity/parasite_piglin_brute_lvl2.png
resource_pack/textures/entity/parasite_piglin_brute_lvl3.png
resource_pack/textures/entity/parasite_piglin_brute_lvl4.png
resource_pack/textures/entity/parasite_piglin_brute_lvl5.png
resource_pack/textures/entity/parasite_piglin_brute_lvl6.png
resource_pack/textures/entity/parasite_piglin_brute_lvl7.png
resource_pack/textures/entity/parasite_pillager_lvl1.png
resource_pack/textures/entity/parasite_pillager_lvl2.png
resource_pack/textures/entity/parasite_pillager_lvl3.png
resource_pack/textures/entity/parasite_pillager_lvl4.png
resource_pack/textures/entity/parasite_pillager_lvl5.png
resource_pack/textures/entity/parasite_pillager_lvl6.png
resource_pack/textures/entity/parasite_pillager_lvl7.png
resource_pack/textures/entity/parasite_shulker_lvl1.png
resource_pack/textures/entity/parasite_shulker_lvl2.png
resource_pack/textures/entity/parasite_shulker_lvl3.png
resource_pack/textures/entity/parasite_shulker_lvl4.png
resource_pack/textures/entity/parasite_shulker_lvl5.png
resource_pack/textures/entity/parasite_shulker_lvl6.png
resource_pack/textures/entity/parasite_shulker_lvl7.png
resource_pack/textures/entity/parasite_slime_lvl1.png
resource_pack/textures/entity/parasite_slime_lvl2.png
resource_pack/textures/entity/parasite_slime_lvl3.png
resource_pack/textures/entity/parasite_slime_lvl4.png
resource_pack/textures/entity/parasite_slime_lvl5.png
resource_pack/textures/entity/parasite_slime_lvl6.png
resource_pack/textures/entity/parasite_slime_lvl7.png
resource_pack/textures/entity/parasite_vex_lvl1.png
resource_pack/textures/entity/parasite_vex_lvl2.png
resource_pack/textures/entity/parasite_vex_lvl3.png
resource_pack/textures/entity/parasite_vex_lvl4.png
resource_pack/textures/entity/parasite_vex_lvl5.png
resource_pack/textures/entity/parasite_vex_lvl6.png
resource_pack/textures/entity/parasite_vex_lvl7.png
resource_pack/textures/entity/parasite_vindicator_lvl1.png
resource_pack/textures/entity/parasite_vindicator_lvl2.png
resource_pack/textures/entity/parasite_vindicator_lvl3.png
resource_pack/textures/entity/parasite_vindicator_lvl4.png
resource_pack/textures/entity/parasite_vindicator_lvl5.png
resource_pack/textures/entity/parasite_vindicator_lvl6.png
resource_pack/textures/entity/parasite_vindicator_lvl7.png
resource_pack/textures/entity/parasite_zoglin_lvl1.png
resource_pack/textures/entity/parasite_zoglin_lvl2.png
resource_pack/textures/entity/parasite_zoglin_lvl3.png
resource_pack/textures/entity/parasite_zoglin_lvl4.png
resource_pack/textures/entity/parasite_zoglin_lvl5.png
resource_pack/textures/entity/parasite_zoglin_lvl6.png
resource_pack/textures/entity/parasite_zoglin_lvl7.png
resource_pack/textures/entity/parasite_ender_dragon_lvl1.png
resource_pack/textures/entity/parasite_ender_dragon_lvl2.png
resource_pack/textures/entity/parasite_ender_dragon_lvl3.png
resource_pack/textures/entity/parasite_ender_dragon_lvl4.png
resource_pack/textures/entity/parasite_ender_dragon_lvl5.png
resource_pack/textures/entity/parasite_ender_dragon_lvl6.png
resource_pack/textures/entity/parasite_ender_dragon_lvl7.png
resource_pack/textures/entity/parasite_axolotl_lvl1.png
resource_pack/textures/entity/parasite_axolotl_lvl2.png
resource_pack/textures/entity/parasite_axolotl_lvl3.png
resource_pack/textures/entity/parasite_axolotl_lvl4.png
resource_pack/textures/entity/parasite_axolotl_lvl5.png
resource_pack/textures/entity/parasite_axolotl_lvl6.png
resource_pack/textures/entity/parasite_axolotl_lvl7.png
resource_pack/textures/entity/parasite_allay_lvl1.png
resource_pack/textures/entity/parasite_allay_lvl2.png
resource_pack/textures/entity/parasite_allay_lvl3.png
resource_pack/textures/entity/parasite_allay_lvl4.png
resource_pack/textures/entity/parasite_allay_lvl5.png
resource_pack/textures/entity/parasite_allay_lvl6.png
resource_pack/textures/entity/parasite_allay_lvl7.png
resource_pack/textures/entity/parasite_armadillo_lvl1.png
resource_pack/textures/entity/parasite_armadillo_lvl2.png
resource_pack/textures/entity/parasite_armadillo_lvl3.png
resource_pack/textures/entity/parasite_armadillo_lvl4.png
resource_pack/textures/entity/parasite_armadillo_lvl5.png
resource_pack/textures/entity/parasite_armadillo_lvl6.png
resource_pack/textures/entity/parasite_armadillo_lvl7.png
resource_pack/textures/items/antibiotic_sword.png
resource_pack/textures/items/corrosive_bow.png
resource_pack/textures/items/bio_spear.png
resource_pack/textures/items/parasite_biomass.png
resource_pack/textures/items/mutagen_core.png
resource_pack/textures/items/boss_relic.png
resource_pack/textures/items/book_purificacion_1.png
resource_pack/textures/items/book_antibiotico_1.png
resource_pack/textures/items/book_disrupcion_1.png
resource_pack/textures/items/book_exterminio.png
resource_pack/textures/items/book_inmunidad_1.png
resource_pack/textures/items/book_bioblindaje_1.png
resource_pack/textures/items/book_regeneracion_1.png
resource_pack/textures/items/radio_ore.png
resource_pack/textures/items/radio_ingot.png
resource_pack/textures/items/book_radio_01.png
resource_pack/textures/items/book_radio_02.png
resource_pack/textures/items/book_radio_03.png
resource_pack/textures/items/book_radio_04.png
resource_pack/textures/items/book_radio_05.png
resource_pack/textures/items/book_radio_06.png
resource_pack/textures/items/book_radio_07.png
resource_pack/textures/items/book_radio_08.png
resource_pack/textures/items/book_radio_09.png
resource_pack/textures/items/book_radio_10.png
resource_pack/textures/items/book_radio_11.png
resource_pack/textures/items/book_radio_12.png
resource_pack/textures/items/book_radio_13.png
resource_pack/textures/items/book_radio_14.png
resource_pack/textures/items/book_radio_15.png
resource_pack/textures/items/book_radio_16.png
resource_pack/textures/items/book_radio_17.png
resource_pack/textures/items/book_radio_18.png
resource_pack/textures/items/book_radio_19.png
resource_pack/textures/items/book_radio_20.png
resource_pack/textures/items/book_radio_21.png
resource_pack/textures/items/book_radio_22.png
resource_pack/textures/items/book_radio_23.png
resource_pack/textures/items/book_radio_24.png
resource_pack/textures/items/book_radio_25.png
resource_pack/textures/items/radio_weapon_01.png
resource_pack/textures/items/radio_weapon_02.png
resource_pack/textures/items/radio_weapon_03.png
resource_pack/textures/items/radio_weapon_04.png
resource_pack/textures/items/radio_weapon_05.png
resource_pack/textures/items/radio_weapon_06.png
resource_pack/textures/items/radio_weapon_07.png
resource_pack/textures/items/radio_weapon_08.png
resource_pack/textures/items/radio_weapon_09.png
resource_pack/textures/items/radio_weapon_10.png
resource_pack/textures/items/radio_weapon_11.png
resource_pack/textures/items/radio_weapon_12.png
resource_pack/textures/items/radio_weapon_13.png
resource_pack/textures/items/radio_weapon_14.png
resource_pack/textures/items/radio_weapon_15.png
resource_pack/textures/items/radio_weapon_16.png
resource_pack/textures/items/radio_weapon_17.png
resource_pack/textures/items/radio_weapon_18.png
resource_pack/textures/items/radio_weapon_19.png
resource_pack/textures/items/radio_weapon_20.png
resource_pack/textures/items/radio_weapon_21.png
resource_pack/textures/items/radio_weapon_22.png
resource_pack/textures/items/radio_weapon_23.png
resource_pack/textures/items/radio_weapon_24.png
resource_pack/textures/items/radio_weapon_25.png
resource_pack/textures/armor/parasite_helmet.png
resource_pack/textures/armor/parasite_chestplate.png
resource_pack/textures/armor/parasite_leggings.png
resource_pack/textures/armor/parasite_boots.png
resource_pack/textures/armor/radio_armor_01.png
resource_pack/textures/armor/radio_armor_02.png
resource_pack/textures/armor/radio_armor_03.png
resource_pack/textures/armor/radio_armor_04.png
resource_pack/textures/armor/radio_armor_05.png
resource_pack/textures/armor/radio_armor_06.png
resource_pack/textures/armor/radio_armor_07.png
resource_pack/textures/armor/radio_armor_08.png
resource_pack/textures/armor/radio_armor_09.png
resource_pack/textures/armor/radio_armor_10.png
resource_pack/textures/armor/radio_armor_11.png
resource_pack/textures/armor/radio_armor_12.png
resource_pack/textures/armor/radio_armor_13.png
resource_pack/textures/armor/radio_armor_14.png
resource_pack/textures/armor/radio_armor_15.png
resource_pack/textures/armor/radio_armor_16.png
resource_pack/textures/armor/radio_armor_17.png
resource_pack/textures/armor/radio_armor_18.png
resource_pack/textures/armor/radio_armor_19.png
resource_pack/textures/armor/radio_armor_20.png
resource_pack/textures/armor/radio_armor_21.png
resource_pack/textures/armor/radio_armor_22.png
resource_pack/textures/armor/radio_armor_23.png
resource_pack/textures/armor/radio_armor_24.png
resource_pack/textures/armor/radio_armor_25.png
resource_pack/textures/models/armor/parasite_layer_1.png
resource_pack/textures/models/armor/parasite_layer_2.png
```

**Sonidos (OGG)**
```
resource_pack/sounds/parasite_attack.ogg
resource_pack/sounds/parasite_death.ogg
resource_pack/sounds/parasite_evolve.ogg
```

## 🔧 Instalación
1. Copia **behavior_pack/** y **resource_pack/** a:
   - Windows: `%LOCALAPPDATA%\Packages\Microsoft.MinecraftUWP...\LocalState\games\com.mojang\development_*_packs`
   - Android: `games/com.mojang/development_*_packs`
2. Activa ambos packs desde el menú de **Add-Ons** en tu mundo.
3. Genera parásitos con `/summon addon:parasite_lvl1` o invoca la flor con `/summon addon:parasite_bloom`.
4. (Opcional) Activa fases con `/summon addon:world_phase_controller_lvl1`.

## 🧪 Ajustes recomendados
- Ajusta valores de daño/vida en `behavior_pack/entities/parasite_lvl*.json` según tu dificultad.
- Personaliza sonidos y texturas agregando los archivos binarios en `resource_pack/`.

## ⚠️ Notas técnicas
- No usa scripts experimentales.
- Los encantamientos se aplican mediante tags e items especiales (libros). Puedes integrarlos con sistemas de encantamiento vanilla vía funciones si lo deseas.

