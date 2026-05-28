````md id="lab18viewmodel"
# LAB 18 — ViewModel et LiveData Android

![Android](https://img.shields.io/badge/Platform-Android-green)
![Jetpack](https://img.shields.io/badge/Jetpack-LiveData-blue)
![MVVM](https://img.shields.io/badge/Architecture-MVVM-orange)

## 📌 Description

Ce laboratoire présente l’utilisation de :

- ViewModel
- LiveData
- Observer
- LifecycleOwner

pour gérer correctement les changements de configuration Android.

---

# 🎯 Objectifs

- comprendre la rotation d’écran ;
- éviter la perte de données ;
- utiliser ViewModel ;
- observer les données avec LiveData ;
- maîtriser le cycle de vie Android.

---

# ⚙️ Technologies

- Android Studio
- Java
- Android Jetpack
- LiveData
- ViewModel

---

# 🚀 Étape 1 — Dépendances

Dans `build.gradle`

```gradle id="w9m2pl"
implementation "androidx.lifecycle:lifecycle-viewmodel:2.8.0"
implementation "androidx.lifecycle:lifecycle-livedata:2.8.0"
````

---

# ❌ Partie 1 — Sans ViewModel

Exemple classique :

```java id="u3x7rk"
int counter = 0;
```

Problème :

* données perdues après rotation ;
* Activity recréée.

---

# ✅ Partie 2 — Avec ViewModel

Créer :

```java id="n6q1vt"
public class CounterViewModel
extends ViewModel {

}
```
<img width="378" height="820" alt="image" src="https://github.com/user-attachments/assets/98da80a5-005f-47ac-8022-aac9a58f09f5" />

---

# 🔄 MutableLiveData

Exemple :

```java id="f4m8ps"
MutableLiveData<Integer> counter =
new MutableLiveData<>(0);
```

---

# 👀 Observer LiveData

```java id="r8x5wl"
viewModel.counter.observe(
this,
value -> {

    txt.setText(
    String.valueOf(value)
    );
});
```

---

# ➕ Modifier Valeur

```java id="q1v6mn"
counter.setValue(
counter.getValue() + 1
);
```
<img width="472" height="1024" alt="image" src="https://github.com/user-attachments/assets/3524bc87-1f91-4cc8-bfd2-13a873f8b188" />

---

# 📱 MainActivity

Connexion ViewModel :

```java id="j5p2xt"
CounterViewModel viewModel =
new ViewModelProvider(this)
.get(CounterViewModel.class);
```
<img width="472" height="1024" alt="image" src="https://github.com/user-attachments/assets/d0d8f840-f671-4d85-a610-4c16b14bcf6c" />

---

# 🧪 Tests

Tester :

* rotation écran ;
* changement thème ;
* pause/reprise app ;
* background thread.

---

# 📊 Comparaison

| Sans ViewModel        | Avec ViewModel      |
| --------------------- | ------------------- |
| données perdues       | données conservées  |
| logique dans Activity | logique séparée     |
| mauvaise architecture | architecture propre |

---

# 📚 Concepts Appris

* ViewModel
* LiveData
* Observer
* LifecycleOwner
* MVVM

---

# ⚠️ Bonnes Pratiques

* éviter logique dans Activity ;
* utiliser LiveData immutable ;
* observer selon cycle de vie ;
* utiliser ViewModel pour état UI.

---

# 👨‍💻 Auteur

Ayoub Laafar — EMSI Marrakech

```
```
