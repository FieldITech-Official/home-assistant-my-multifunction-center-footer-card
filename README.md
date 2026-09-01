# 🏠 Carte Multifonction Home Assistant (Button Card)

Ce dépôt fournit la configuration YAML pour déployer une carte de tableau de bord hautement personnalisable et dynamique sous **Home Assistant** à l'aide de la **`custom:button-card`**. Ce système intègre un en-tête avec badge de présence, un bloc central interactif (température, humidité, navigation de pièce) et un pied de page modulable par grille pour regrouper l'ensemble de vos entités.

## 🛠️ Caractéristiques et Composants

* **En-tête dynamique** : Titre de la pièce personnalisable et badge de présence interactif (`more-info` au clic).
* **Bloc Central Interactif** : Affichage optionnel de la température et de l'humidité avec code couleur, et icône principale cliquable redirigée vers une vue dédiée.
* **Pied de page modulaire par grille** : De 1 à 12 slots d'entités entièrement configurables avec gestion dynamique des états (actifs/inactifs, capteurs numériques ou binaires).
* **Affichage conditionnel** : Paramètres globaux pour afficher ou masquer à la volée le bloc central et le pied de page (`show_center`, `show_footer`).

---

## 🚀 Instructions d'installation

1. Vérifiez que la carte personnalisée **`custom:button-card`** est bien installée sur votre instance Home Assistant (disponible via HACS).
2. Copiez le contenu du fichier `card.yaml` dans une carte manuelle de votre tableau de bord Lovelace ou dans un fichier de modèle.
3. Adaptez les variables globales (`title`, `navigation_path`, `presence`, `temperature`, `humidity`) ainsi que les entités du footer selon vos propres équipements.

---

### [card.yaml](./card.yaml)
```yaml
# --------------------------------------------------------------------------------
# Created by Fielditech - [https://fielditech.com](https://fielditech.com)
# Configuration de ma carte pour Home Assistant avec button-card
# Support me: [buymeacoffee.com/fielditech](https://buymeacoffee.com/fielditech)
# --------------------------------------------------------------------------------
type: custom:button-card
variables:
  # ==========================================
  # CONFIGURATION GLOBALE DE LA CARTE
  # ==========================================
  title: Cuisine                          # Titre affiché en haut de la carte
  navigation_path: /lovelace/cuisine      # Lien de redirection au clic sur l'icône principale
  main_icon: mdi:countertop-outline       # Icône principale au centre de la carte
  
  presence: binary_sensor.fictional_presence     # Entité pour le badge de présence (haut droit)
  temperature: sensor.fictional_temperature      # Entité capteur pour la température (centre)
  humidity: sensor.fictional_humidity            # Entité capteur pour l'humidité (centre)

  # ==========================================
  # VISIBILITÉ DES BLOCS (true = affiché, false = masqué)
  # ==========================================
  show_center: true                       # true pour afficher le bloc central (icône + température/humidité) / false pour le masquer
  show_footer: true                       # true pour afficher le pied de page (les slots d'entités) / false pour le masquer
  
  footer_count: 7                         # Nombre total de slots à afficher dans le footer (de 1 à 12)
  footer_layout:                          # Disposition des slots par ligne (ex: 1 sur la 1ère ligne, 4 sur la 2ème, 3 sur la 3ème)
    - 1
    - 4
    - 3

  # ==========================================
  # CONFIGURATION DES SLOTS DU FOOTER (1 à 12)
  # ==========================================
  
  # --- SLOT 1 : Capteur numérique (ex: Luminosité) ---
  entity_1: sensor.fictional_illuminance
  slot_1_name: Luminosité
  slot_1_icon: mdi:brightness-5
  slot_1_accent: '#ffd60a'
  slot_1_unit: Lux

  # --- SLOT 2 : Capteur binaire (ex: Détecteur de fumée) ---
  entity_2: binary_sensor.fictional_smoke_alarm
  slot_2_name: Fumée
  slot_2_icon: mdi:smoke-detector-variant
  slot_2_accent: '#ff3b30'
  slot_2_active_state: 'on'               # État de l'entité qui déclenche la couleur active ('on', 'open', etc.)
  slot_2_label_active: Détectée !         # Texte affiché lorsque l'entité est active
  slot_2_label_inactive: Normal           # Texte affiché lorsque l'entité est inactive

  # --- SLOT 3 : Appareil / Éclairage (ex: Lampe) ---
  entity_3: light.fictional_light
  slot_3_name: Lampe
  slot_3_icon: mdi:lightbulb
  slot_3_accent: '#00f2fe'
  slot_3_active_state: 'on'
  slot_3_label_active: Allumée
  slot_3_label_inactive: Éteinte

  # --- SLOT 4 : Autre appareil / capteur ---
  entity_4: binary_sensor.fictional_slot_4
  slot_4_name: Autre 4
  slot_4_icon: mdi:eye-check
  slot_4_accent: '#a855f7'
  slot_4_active_state: 'on'
  slot_4_label_active: Actif
  slot_4_label_inactive: Inactif

  # --- SLOT 5 : Autre appareil / capteur ---
  entity_5: binary_sensor.fictional_slot_5
  slot_5_name: Autre 5
  slot_5_icon: mdi:power-plug
  slot_5_accent: '#3b82f6'
  slot_5_active_state: 'on'
  slot_5_label_active: Actif
  slot_5_label_inactive: Inactif

  # --- SLOT 6 : Autre appareil / capteur ---
  entity_6: binary_sensor.fictional_slot_6
  slot_6_name: Autre 6
  slot_6_icon: mdi:window-closed
  slot_6_accent: '#10b981'
  slot_6_active_state: 'on'
  slot_6_label_active: Actif
  slot_6_label_inactive: Inactif

  # --- SLOT 7 : Autre appareil / capteur ---
  entity_7: binary_sensor.fictional_slot_7
  slot_7_name: Autre 7
  slot_7_icon: mdi:chip
  slot_7_accent: '#ec4899'
  slot_7_active_state: 'on'
  slot_7_label_active: Actif
  slot_7_label_inactive: Inactif

  # --- SLOT 8 : Autre appareil / capteur ---
  entity_8: binary_sensor.fictional_slot_8
  slot_8_name: Autre 8
  slot_8_icon: mdi:chip
  slot_8_accent: '#f59e0b'
  slot_8_active_state: 'on'
  slot_8_label_active: Actif
  slot_8_label_inactive: Inactif

  # --- SLOT 9 : Autre appareil / capteur ---
  entity_9: binary_sensor.fictional_slot_9
  slot_9_name: Autre 9
  slot_9_icon: mdi:chip
  slot_9_accent: '#14b8a6'
  slot_9_active_state: 'on'
  slot_9_label_active: Actif
  slot_9_label_inactive: Inactif

  # --- SLOT 10 : Autre appareil / capteur ---
  entity_10: binary_sensor.fictional_slot_10
  slot_10_name: Autre 10
  slot_10_icon: mdi:chip
  slot_10_accent: '#8b5cf6'
  slot_10_active_state: 'on'
  slot_10_label_active: Actif
  slot_10_label_inactive: Inactif

  # --- SLOT 11 : Autre appareil / capteur ---
  entity_11: binary_sensor.fictional_slot_11
  slot_11_name: Autre 11
  slot_11_icon: mdi:chip
  slot_11_accent: '#eab308'
  slot_11_active_state: 'on'
  slot_11_label_active: Actif
  slot_11_label_inactive: Inactif

  # --- SLOT 12 : Autre appareil / capteur ---
  entity_12: binary_sensor.fictional_slot_12
  slot_12_name: Autre 12
  slot_12_icon: mdi:chip
  slot_12_accent: '#06b6d4'
  slot_12_active_state: 'on'
  slot_12_label_active: Actif
  slot_12_label_inactive: Inactif

show_name: false
show_icon: false
show_state: false
styles:
  card:
    - background: 'radial-gradient(circle at 50% 0%, #151d2a 0%, #080b11 100%)'
    - border-radius: 28px
    - border: 1px solid rgba(0, 242, 254, 0.3)
    - box-shadow: 0 15px 35px rgba(0,0,0,0.8), inset 0 1px 1px rgba(255,255,255,0.1)
    - padding: 20px
    - overflow: visible
    - min-height: 340px
  grid:
    - grid-template-areas: '"header" "center" "footer"'
    - grid-template-rows: |
        [[[
          return variables.show_center !== false ? 'auto 1fr auto' : 'auto auto auto';
        ]]]
    - align-content: start
    - gap: 14px
tap_action:
  action: none
custom_fields:
  header:
    card:
      type: custom:button-card
      styles:
        card:
          - background: transparent
          - border: none
          - border-bottom: 2px solid rgba(255, 255, 255, 0.08)
          - padding-bottom: 12px
          - box-shadow: none
          - padding: 0px 0px 12px 0px
          - overflow: visible
        grid:
          - grid-template-areas: '"title status"'
          - grid-template-columns: 1fr auto
          - align-items: center
          - justify-content: space-between
      custom_fields:
        title: >
          [[[ return `<div style="font-weight: 900; font-size: 20px;
          letter-spacing: 1.5px; color: #ffffff; text-align: left; display:
          flex; align-items: center; height: 100%;">${variables.title}</div>`;
          ]]]
        status:
          card:
            type: custom:button-card
            entity: '[[[ return variables.presence; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: false
            icon: mdi:circle
            name: Présence détectée
            styles:
              card:
                - background: rgba(0, 242, 254, 0.12)
                - border: 1px solid rgba(0, 242, 254, 0.4)
                - border-radius: 20px
                - padding: 3px 10px
                - cursor: pointer
                - box-shadow: none
                - width: fit-content
                - justify-self: end
              grid:
                - grid-template-areas: '"i n"'
                - grid-template-columns: auto 1fr
                - align-items: center
              icon:
                - color: |
                    [[[
                      const ent = states[variables.presence];
                      return (ent && ent.state === 'on') ? '#22c55e' : '#64748b';
                    ]]]
                - width: 15px
                - margin-right: 10px
              name:
                - font-size: 15px
                - color: '#00f2fe'
                - font-weight: '800'
  center:
    card:
      type: custom:button-card
      styles:
        card:
          - background: transparent
          - border: none
          - box-shadow: none
          - padding: 0px
          - overflow: hidden
          - height: |
              [[[
                return variables.show_center !== false ? 'auto' : '0px';
              ]]]
        grid:
          - grid-template-areas: '"icon_main telemetry"'
          - grid-template-columns: 1fr 1.3fr
          - gap: 14px
          - align-items: center
      custom_fields:
        icon_main:
          card:
            type: custom:button-card
            icon: '[[[ return variables.main_icon; ]]]'
            size: 52px
            show_icon: true
            show_name: false
            show_state: false
            tap_action:
              action: navigate
              navigation_path: '[[[ return variables.navigation_path; ]]]'
            styles:
              card:
                - background: >-
                    linear-gradient(135deg, rgba(0,242,254,0.12) 0%,
                    rgba(0,242,254,0.02) 100%)
                - border: 1px solid rgba(255, 255, 255, 0.06)
                - border-radius: 20px
                - height: 120px
                - display: flex
                - align-items: center
                - justify-content: center
                - cursor: pointer
              icon:
                - color: '#00f2fe'
                - filter: drop-shadow(0px 0px 10px rgba(0,242,254,0.8))
        telemetry:
          card:
            type: custom:button-card
            styles:
              card:
                - background: transparent
                - border: none
                - box-shadow: none
                - padding: 0px
              grid:
                - grid-template-areas: '"temp" "hum"'
                - grid-template-rows: repeat(2, 1fr)
                - gap: 10px
            custom_fields:
              temp:
                card:
                  type: custom:button-card
                  entity: '[[[ return variables.temperature; ]]]'
                  tap_action:
                    action: more-info
                  show_name: false
                  show_icon: true
                  show_state: true
                  icon: mdi:thermometer
                  state_display: |
                    [[[
                      const ent = states[variables.temperature];
                      if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'N/A';
                      const unit = ent.attributes.unit_of_measurement || '';
                      return `${ent.state} ${unit}`;
                    ]]]
                  styles:
                    card:
                      - background: rgba(0, 0, 0, 0.45)
                      - border: 1px solid rgba(255, 255, 255, 0.08)
                      - border-left: '4px solid #ff9f0a'
                      - border-radius: 12px
                      - padding: 12px 14px
                      - cursor: pointer
                    grid:
                      - grid-template-areas: '"i s"'
                      - grid-template-columns: auto 1fr
                      - align-items: center
                      - justify-content: space-between
                    icon:
                      - color: '#ffffff'
                      - width: 28px
                    state:
                      - font-size: 22px
                      - font-weight: '900'
                      - color: '#ff9f0a'
                      - text-align: right
              hum:
                card:
                  type: custom:button-card
                  entity: '[[[ return variables.humidity; ]]]'
                  tap_action:
                    action: more-info
                  show_name: false
                  show_icon: true
                  show_state: true
                  icon: mdi:water-percent
                  state_display: |
                    [[[
                      const ent = states[variables.humidity];
                      if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'N/A';
                      const unit = ent.attributes.unit_of_measurement || '';
                      return `${ent.state} ${unit}`;
                    ]]]
                  styles:
                    card:
                      - background: rgba(0, 0, 0, 0.45)
                      - border: 1px solid rgba(255, 255, 255, 0.08)
                      - border-left: '4px solid #00f2fe'
                      - border-radius: 12px
                      - padding: 12px 14px
                      - cursor: pointer
                    grid:
                      - grid-template-areas: '"i s"'
                      - grid-template-columns: auto 1fr
                      - align-items: center
                      - justify-content: space-between
                    icon:
                      - color: '#ffffff'
                      - width: 28px
                    state:
                      - font-size: 22px
                      - font-weight: '900'
                      - color: '#00f2fe'
                      - text-align: right
  footer:
    card:
      type: custom:button-card
      styles:
        card:
          - background: transparent
          - border: none
          - box-shadow: none
          - padding: 0px
          - overflow: hidden
          - height: |
              [[[
                return variables.show_footer !== false ? 'auto' : '0px';
              ]]]
        grid:
          - grid-template-areas: |
              [[[
                let count = variables.footer_count || 4;
                let allKeys = ['slot_1', 'slot_2', 'slot_3', 'slot_4', 'slot_5', 'slot_6', 'slot_7', 'slot_8', 'slot_9', 'slot_10', 'slot_11', 'slot_12'];
                let keys = allKeys.slice(0, count);
                let orphanKeys = allKeys.slice(count);

                let layout = (variables.footer_layout && variables.footer_layout.length) ? variables.footer_layout : [2, 2];
                let rows = [];
                let currentIndex = 0;

                for (let rc of layout) {
                  if (currentIndex >= keys.length) break;
                  let chunk = keys.slice(currentIndex, currentIndex + rc);
                  if (chunk.length > 0) {
                    rows.push(chunk);
                    currentIndex += chunk.length;
                  }
                }

                while (currentIndex < keys.length) {
                  let chunk = keys.slice(currentIndex, currentIndex + 3);
                  rows.push(chunk);
                  currentIndex += chunk.length;
                }

                if (rows.length === 0 && orphanKeys.length === 0) return '"none"';

                let maxCols = rows.length ? (Math.max(...rows.map(r => r.length)) || 1) : 3;

                let areas = rows.map(row => {
                  let r = [...row];
                  while(r.length < maxCols) {
                    r.push(r[r.length - 1]);
                  }
                  return `"${r.join(' ')}"`;
                });

                let oIndex = 0;
                while (oIndex < orphanKeys.length) {
                  let chunk = orphanKeys.slice(oIndex, oIndex + maxCols);
                  while (chunk.length < maxCols) {
                    chunk.push(chunk[chunk.length - 1]);
                  }
                  areas.push(`"${chunk.join(' ')}"`);
                  oIndex += maxCols;
                }

                return areas.join(' ');
              ]]]
          - grid-template-columns: |
              [[[
                let count = variables.footer_count || 4;
                let allKeys = ['slot_1', 'slot_2', 'slot_3', 'slot_4', 'slot_5', 'slot_6', 'slot_7', 'slot_8', 'slot_9', 'slot_10', 'slot_11', 'slot_12'];
                let keys = allKeys.slice(0, count);
                let layout = (variables.footer_layout && variables.footer_layout.length) ? variables.footer_layout : [2, 2];
                let rows = [];
                let currentIndex = 0;

                for (let rc of layout) {
                  if (currentIndex >= keys.length) break;
                  let chunk = keys.slice(currentIndex, currentIndex + rc);
                  if (chunk.length > 0) {
                    rows.push(chunk);
                    currentIndex += chunk.length;
                  }
                }
                while (currentIndex < keys.length) {
                  let chunk = keys.slice(currentIndex, currentIndex + 3);
                  rows.push(chunk);
                  currentIndex += chunk.length;
                }

                if (rows.length === 0) return '1fr';

                let maxCols = Math.max(...rows.map(r => r.length)) || 1;
                return `repeat(${maxCols}, 1fr)`;
              ]]]
          - gap: 10px
      custom_fields:
        slot_1:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_1; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_1_icon; ]]]'
            name: '[[[ return variables.slot_1_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_1];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'N/A';
                return `${ent.state} <span style="color: ${variables.slot_1_accent};">${variables.slot_1_unit || ''}</span>`;
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: '[[[ return `3px solid ${variables.slot_1_accent}`; ]]]'
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 1 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: '[[[ return variables.slot_1_accent; ]]]'
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: '#ffffff'
        slot_2:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_2; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            name: '[[[ return variables.slot_2_name; ]]]'
            icon: '[[[ return variables.slot_2_icon; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_2];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_2_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_2_label_active || 'Actif')
                  : (variables.slot_2_label_inactive || 'Normal');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_2];
                      const active = variables.slot_2_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_2_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 2 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_2];
                      const active = variables.slot_2_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_2_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_2];
                      const active = variables.slot_2_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_2_accent;
                      return '#ffffff';
                    ]]]
        slot_3:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_3; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_3_icon; ]]]'
            name: '[[[ return variables.slot_3_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_3];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_3_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_3_label_active || 'Actif')
                  : (variables.slot_3_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_3];
                      const active = variables.slot_3_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_3_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 3 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_3];
                      const active = variables.slot_3_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_3_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_3];
                      const active = variables.slot_3_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_3_accent;
                      return '#ffffff';
                    ]]]
        slot_4:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_4; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_4_icon; ]]]'
            name: '[[[ return variables.slot_4_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_4];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_4_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_4_label_active || 'Actif')
                  : (variables.slot_4_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_4];
                      const active = variables.slot_4_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_4_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 4 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_4];
                      const active = variables.slot_4_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_4_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_4];
                      const active = variables.slot_4_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_4_accent;
                      return '#ffffff';
                    ]]]
        slot_5:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_5; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_5_icon; ]]]'
            name: '[[[ return variables.slot_5_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_5];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_5_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_5_label_active || 'Actif')
                  : (variables.slot_5_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_5];
                      const active = variables.slot_5_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_5_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 5 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_5];
                      const active = variables.slot_5_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_5_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_5];
                      const active = variables.slot_5_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_5_accent;
                      return '#ffffff';
                    ]]]
        slot_6:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_6; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_6_icon; ]]]'
            name: '[[[ return variables.slot_6_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_6];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_6_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_6_label_active || 'Actif')
                  : (variables.slot_6_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_6];
                      const active = variables.slot_6_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_6_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 6 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_6];
                      const active = variables.slot_6_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_6_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_6];
                      const active = variables.slot_6_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_6_accent;
                      return '#ffffff';
                    ]]]
        slot_7:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_7; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_7_icon; ]]]'
            name: '[[[ return variables.slot_7_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_7];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_7_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_7_label_active || 'Actif')
                  : (variables.slot_7_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_7];
                      const active = variables.slot_7_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_7_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 7 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_7];
                      const active = variables.slot_7_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_7_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_7];
                      const active = variables.slot_7_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_7_accent;
                      return '#ffffff';
                    ]]]
        slot_8:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_8; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_8_icon; ]]]'
            name: '[[[ return variables.slot_8_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_8];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_8_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_8_label_active || 'Actif')
                  : (variables.slot_8_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_8];
                      const active = variables.slot_8_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_8_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 8 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_8];
                      const active = variables.slot_8_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_8_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_8];
                      const active = variables.slot_8_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_8_accent;
                      return '#ffffff';
                    ]]]
        slot_9:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_9; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_9_icon; ]]]'
            name: '[[[ return variables.slot_9_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_9];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_9_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_9_label_active || 'Actif')
                  : (variables.slot_9_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_9];
                      const active = variables.slot_9_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_9_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 9 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_9];
                      const active = variables.slot_9_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_9_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_9];
                      const active = variables.slot_9_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_9_accent;
                      return '#ffffff';
                    ]]]
        slot_10:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_10; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_10_icon; ]]]'
            name: '[[[ return variables.slot_10_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_10];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_10_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_10_label_active || 'Actif')
                  : (variables.slot_10_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_10];
                      const active = variables.slot_10_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_10_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 10 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_10];
                      const active = variables.slot_10_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_10_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_10];
                      const active = variables.slot_10_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_10_accent;
                      return '#ffffff';
                    ]]]
        slot_11:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_11; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_11_icon; ]]]'
            name: '[[[ return variables.slot_11_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_11];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_11_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_11_label_active || 'Actif')
                  : (variables.slot_11_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_11];
                      const active = variables.slot_11_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_11_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 11 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_11];
                      const active = variables.slot_11_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_11_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_11];
                      const active = variables.slot_11_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_11_accent;
                      return '#ffffff';
                    ]]]
        slot_12:
          card:
            type: custom:button-card
            entity: '[[[ return variables.entity_12; ]]]'
            tap_action:
              action: more-info
            show_name: true
            show_icon: true
            show_state: true
            icon: '[[[ return variables.slot_12_icon; ]]]'
            name: '[[[ return variables.slot_12_name; ]]]'
            state_display: |
              [[[
                const ent = states[variables.entity_12];
                if (!ent || ent.state === 'unavailable' || ent.state === 'unknown') return 'Indisponible';
                const active = variables.slot_12_active_state || 'on';
                return ent.state === active
                  ? (variables.slot_12_label_active || 'Actif')
                  : (variables.slot_12_label_inactive || 'Inactif');
              ]]]
            styles:
              card:
                - background: rgba(0, 0, 0, 0.45)
                - border: 1px solid rgba(255, 255, 255, 0.08)
                - border-top: |
                    [[[
                      const ent = states[variables.entity_12];
                      const active = variables.slot_12_active_state || 'on';
                      if (ent && ent.state === active) return `3px solid ${variables.slot_12_accent}`;
                      return '3px solid #64748b';
                    ]]]
                - border-radius: 12px
                - padding: 10px 8px
                - cursor: pointer
                - display: >
                    [[[ return variables.footer_count >= 12 ? 'flex' : 'none';
                    ]]]
              icon:
                - color: |
                    [[[
                      const ent = states[variables.entity_12];
                      const active = variables.slot_12_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_12_accent;
                      return '#ffffff';
                    ]]]
                - width: 20px
                - margin-bottom: 2px
              name:
                - font-size: 12px
                - color: '#ffffff'
                - font-weight: '800'
                - margin-bottom: 2px
              state:
                - font-size: 14px
                - font-weight: '900'
                - color: |
                    [[[
                      const ent = states[variables.entity_12];
                      const active = variables.slot_12_active_state || 'on';
                      if (ent && ent.state === active) return variables.slot_12_accent;
                      return '#ffffff';
                    ]]]

```

🔗 Liens & Ressources
🌐 Site Web : fielditech.com
