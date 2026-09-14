# Pythonchi 🐍

Барномаи омӯзиши Python аз 0 то 100% — **бе интернет, бе сервер**, бо забони тоҷикӣ (+ русӣ, англисӣ).
Тамоми коркард дар телефон тавассути **Termux** анҷом дода мешавад; сохтани APK бошад тавассути **GitHub Actions**.

## Меъморӣ

- **Flutter** + Clean Architecture (`core/` — умумӣ, `features/*` — ҳар бахш бо `data/domain/presentation`)
- **Riverpod** — идоракунии ҳолат
- **GoRouter** — навигатсия бо `ShellRoute` (панели поёнии 5-tab)
- **Drift (SQLite)** — захираи маҳаллии пешрафт, дарсҳо, дастовардҳо — **ҳама офлайн**
- **flutter_localizations + ARB** — tg (пешфарз), ru, en
- **Playground** — муҳаррири код + интерфейси `PythonInterpreter` (татбиқи воқеӣ дар қадами навбатӣ)

## Насби муҳит дар Termux

```bash
pkg update && pkg upgrade
pkg install git wget unzip openjdk-17

# Flutter SDK (нусхаи стабилӣ)
git clone https://github.com/flutter/flutter.git -b stable ~/flutter
export PATH="$HOME/flutter/bin:$PATH"
echo 'export PATH="$HOME/flutter/bin:$PATH"' >> ~/.bashrc

flutter doctor
```

> Эзоҳ: сохтани APK дар худи Termux одатан кор намекунад (Android SDK/NDK-и пурра лозим аст).
> Барои ҳамин мо **GitHub Actions**-ро истифода мебарем — шумо код push мекунед, CI APK месозад.

## Кор дар Termux

```bash
cd pythonchi

# МУҲИМ: феҳристҳои android/ios дар ин skeleton нестанд (бе Flutter SDK
# сохта намешаванд). Якдафъаина иҷро кунед, то онҳо тавлид шаванд —
# файлҳои lib/pubspec.yaml/l10n мавҷудаатон нигоҳ дошта мешаванд:
flutter create --org com.mahmadsoni --project-name pythonchi .

flutter pub get

# Тавлиди файлҳои generate-шаванда (Drift + l10n)
dart run build_runner build --delete-conflicting-outputs

# Санҷиши хатоҳо бе сохтани APK (тезтар аз build)
flutter analyze
```

## Push ба GitHub (тавассути Termux)

```bash
git init
git add .
git commit -m "Сохтори аввалини Pythonchi"
git branch -M main
git remote add origin https://github.com/mahmadsoni/pythonchi.git
git push -u origin main
```

Баъд аз push, дар таби **Actions**-и GitHub workflow худкор оғоз мешавад ва APK-ро
ҳамчун **Release** ва **Artifact** мебарорад — онро мустақим ба телефон боргирӣ кунед.

## Харитаи роҳ (0% → 100%)

- [x] Сохтори лоиҳа, теми, роутер, l10n (3 забон), Drift schema
- [ ] Interpreter-и воқеии зерқисми Python (Playground)
- [ ] Контенти дарсҳо (модул 1–8, JSON дар `assets/lessons/`)
- [ ] Мантиқи XP/level/streak (Riverpod providers аз Drift)
- [ ] Квизҳо ва санҷиши ҷавобҳо
- [ ] Дастовардҳо (achievement rules)
- [ ] Онбординг (3 экран аввалин)
- [ ] Cӣ ҷиллошавии тарзи рӯшноӣ/торикӣ + иконка/сплэш
