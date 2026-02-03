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

### Evolución
Las entidades usan:
- `component_groups` + `events` para transformación.
- `minecraft:timer` para evolución automática.
- `minecraft:on_kill_entity` para evolución por combate.

### Armas especiales
- **Espada antibiótica**: daño extra vs parásitos.
- **Arco corrosivo**: proyectil con veneno.
- **Lanza biológica**: daño alto y penetrante.

### Armaduras
Set completo anti-parásitos con:
- Reducción de daño biológico.
- Resistencia a infección.
- Bonus de set (propuesto vía tags para eventos).

### Encantamientos personalizados (sistema por tags)
Se implementa un sistema de “encantamientos” usando **tags, eventos y sensores de daño**:
- **Purificación (I–V)**
- **Antibiótico (I–III)**
- **Disrupción Celular (I–II)**
- **Exterminio (único)**
- **Inmunidad (I–IV)**
- **Bioblindaje (I–III)**
- **Regeneración Sintética (I–II)**

> Los libros encantados son ítems dedicados (`addon:book_*`) que otorgan tags usados por los parásitos para activar eventos.

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
resource_pack/textures/armor/parasite_helmet.png
resource_pack/textures/armor/parasite_chestplate.png
resource_pack/textures/armor/parasite_leggings.png
resource_pack/textures/armor/parasite_boots.png
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
3. Genera parásitos con `/summon addon:parasite_lvl1` o deja que aparezcan de noche.

## 🧪 Ajustes recomendados
- Ajusta valores de daño/vida en `behavior_pack/entities/parasite_lvl*.json` según tu dificultad.
- Personaliza sonidos y texturas agregando los archivos binarios en `resource_pack/`.

## ⚠️ Notas técnicas
- No usa scripts experimentales.
- Los encantamientos se aplican mediante tags e items especiales (libros). Puedes integrarlos con sistemas de encantamiento vanilla vía funciones si lo deseas.

