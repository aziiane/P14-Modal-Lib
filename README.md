# Bibliothèque de Modal React

## Fonctionnalités

- 🎨 **Tailles Personnalisables** : Choisissez parmi des tailles prédéfinies (sm, md, lg, xl) ou utilisez des styles personnalisés
- ⌨️ **Support Clavier** : Fermer la modal avec la touche Échap (optionnel)
- 📱 **Design Responsive** : Compatible mobile avec des points de rupture adaptatifs
- 🎭 **Moderne** : Animations de fondu entrant/sortant et de glissement
- 🪝 **Hook Intégré** : Hook `useModalStates` pratique pour la gestion d'état
- 💾 **Support TypeScript** : Support complet de TypeScript avec définitions de types

## Installation

```bash
npm install my-react-modal-oc-p14
```

## Démarrage Rapide

```tsx
import React from "react";
import { Modal, useModalStates } from "my-react-modal-oc-p14";

function App() {
  const { isOpen, onOpen, onClose } = useModalStates();

  return (
    <div>
      <button onClick={onOpen}>Ouvrir la Modal</button>

      <Modal isOpen={isOpen} onClose={onClose} title="Ma Modal">
        <p>Ceci est le contenu de la modal !</p>
      </Modal>
    </div>
  );
}
```

## Référence de l'API

### Composant Modal

#### Props

| Prop | Type | Défaut | Description |
| --- | --- | --- | --- |
| `isOpen` | `boolean` | - | **Requis.** Contrôle si la modal est visible |
| `onClose` | `() => void` | - | **Requis.** Fonction appelée quand la modal doit se fermer |
| `children` | `ReactNode` | - | **Requis.** Contenu à afficher dans la modal |
| `title` | `string` | - | Titre optionnel affiché dans l'en-tête de la modal |
| `size` | `'sm' \| 'md' \| 'lg' \| 'xl'` | `'md'` | Tailles prédéfinies de la modal |
| `closeOnOverlayClick` | `boolean` | `true` | Si cliquer sur l'overlay ferme la modal |
| `closeOnEscape` | `boolean` | `true` | Si appuyer sur Échap ferme la modal |
| `showCloseButton` | `boolean` | `true` | Si afficher le bouton de fermeture X |

#### Options de Taille

- **sm** : 24rem (384px) largeur max
- **md** : 32rem (512px) largeur max
- **lg** : 48rem (768px) largeur max
- **xl** : 64rem (1024px) largeur max

### Hook useModalStates

Un hook pratique pour gérer l'état de la modal.

```tsx
const { isOpen, onOpen, onClose, onToggle } = useModalStates(initialState?);
```

#### Paramètres

- `initialState` (optionnel) : `boolean` - État initial d'ouverture (par défaut `false`)

#### Retourne

| Propriété  | Type         | Description                         |
| ---------- | ------------ | ----------------------------------- |
| `isOpen`   | `boolean`    | État actuel de la modal             |
| `onOpen`   | `() => void` | Fonction pour ouvrir la modal       |
| `onClose`  | `() => void` | Fonction pour fermer la modal       |
| `onToggle` | `() => void` | Fonction pour basculer l'état modal |

## Exemples d'Usage

### Modal de Base

```tsx
import { Modal, useModalStates } from "my-react-modal-oc-p14";

function ExempleDeBase() {
  const { isOpen, onOpen, onClose } = useModalStates();

  return (
    <>
      <button onClick={onOpen}>Ouvrir la Modal</button>
      <Modal isOpen={isOpen} onClose={onClose}>
        <h3>Salut le monde !</h3>
        <p>Ceci est un exemple de modal de base.</p>
      </Modal>
    </>
  );
}
```

### Modal avec Titre et Taille Personnalisée

```tsx
import { Modal, useModalStates } from "my-react-modal-oc-p14";

function ExempleTitre() {
  const { isOpen, onOpen, onClose } = useModalStates();

  return (
    <>
      <button onClick={onOpen}>Ouvrir une Grande Modal</button>
      <Modal isOpen={isOpen} onClose={onClose} title="Paramètres" size="lg">
        <div>
          <h4>Préférences Utilisateur</h4>
          <form>
            <label>
              Email :
              <input type="email" />
            </label>
            <button type="submit">Enregistrer</button>
          </form>
        </div>
      </Modal>
    </>
  );
}
```

### Modals Multiples

```tsx
import { Modal, useModalStates } from "my-react-modal-oc-p14";

function ExempleModalsMultiples() {
  const modal1 = useModalStates();
  const modal2 = useModalStates();

  return (
    <>
      <button onClick={modal1.onOpen}>Ouvrir la Première Modal</button>
      <button onClick={modal2.onOpen}>Ouvrir la Deuxième Modal</button>

      <Modal
        isOpen={modal1.isOpen}
        onClose={modal1.onClose}
        title="Première Modal"
      >
        <p>Ceci est la première modal.</p>
        <button onClick={modal2.onOpen}>Ouvrir la Deuxième Modal</button>
      </Modal>

      <Modal
        isOpen={modal2.isOpen}
        onClose={modal2.onClose}
        title="Deuxième Modal"
        size="sm"
      >
        <p>Ceci est la deuxième modal.</p>
      </Modal>
    </>
  );
}
```

## Dépendances

- React ^19.1.0
- React DOM ^19.1.0

## Licence

Ce projet est sous licence MIT.

## Support

Si vous rencontrez des problèmes ou avez des questions, veuillez ouvrir une issue sur le repository GitHub.
