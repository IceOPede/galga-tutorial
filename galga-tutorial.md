# Galga

## {Einführung @showdialog}

Fliege dein Raumschiff durch die entgegenkommenden feindlichen Raumschiffe. Kannst du den fortlaufenden Angriff überleben? Du startest mit drei Leben, aber du sammelst Punkte, indem du auf die feindlichen Schiffe schießt. Du verlierst ein Leben bei jeder Kollision, also versuche die Feinde zu zerstören, bevor sie dich treffen.

![Space plane and attacking spacecraft](/static/tutorials/galga.gif)

## {Schrit 1}

Füge Code hinzu, um ein ``||sprites:Sprite||`` zu erstellen, benenne es ``||variables(noclick):raumschiff||`` und zeichne ein Flugzeug oder eine Art von Flugobjekt.

![Space plane sprite image](/static/tutorials/galga/space-plane.jpg)

```typescript
let raumschiff = sprites.create(img`
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . 8 2 . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . 1 1 1 . . . . . 9 9 9 9 9 . . . . . . . . . . . . . . .
    . . . . 2 2 2 2 . . . 9 9 9 9 9 9 9 . . . . . . . . . . . . . .
    . 4 4 4 f 8 6 6 6 6 6 6 9 9 9 9 9 6 6 6 . . . . . . . . . . . .
    4 4 4 f 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 . . . . . . . . .
    . 4 4 f 6 8 8 8 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 . . . . . . . .
    . . 4 4 f 8 8 . . . . . 8 8 8 8 6 6 6 6 6 6 6 . . . . . . . . .
    . . . . . . . . . . . 8 8 8 8 8 8 2 . . . . . . . . . . . . . .
    . . . . . . . . . . . 8 8 8 8 8 2 . . . . . . . . . . . . . . .
    . . . . . . . . . . 8 8 8 8 8 2 . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
`, SpriteKind.Player)
```

## {Schrit 2}

Stelle sicher, dass das ``||variables(noclick):raumschiff||`` ``||sprites:im dem Bildschirm bleibt||``.

```typescript
let raumschiff = sprites.create(img`
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . 8 2 . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . 1 1 1 . . . . . 9 9 9 9 9 . . . . . . . . . . . . . . .
    . . . . 2 2 2 2 . . . 9 9 9 9 9 9 9 . . . . . . . . . . . . . .
    . 4 4 4 f 8 6 6 6 6 6 6 9 9 9 9 9 6 6 6 . . . . . . . . . . . .
    4 4 4 f 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 . . . . . . . . .
    . 4 4 f 6 8 8 8 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 . . . . . . . .
    . . 4 4 f 8 8 . . . . . 8 8 8 8 6 6 6 6 6 6 6 . . . . . . . . .
    . . . . . . . . . . . 8 8 8 8 8 8 2 . . . . . . . . . . . . . .
    . . . . . . . . . . . 8 8 8 8 8 2 . . . . . . . . . . . . . . .
    . . . . . . . . . . 8 8 8 8 8 2 . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
`, SpriteKind.Player)
// @highlight
raumschiff.setStayInScreen(true)
```

## {Schrit 3}

Starte das Spiel mit einigen Leben, also stelle die ``||info:Anzahl der Leben||`` auf ``3`` ein.

```typescript
let raumschiff = sprites.create(img`
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . 8 2 . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . 1 1 1 . . . . . 9 9 9 9 9 . . . . . . . . . . . . . . .
    . . . . 2 2 2 2 . . . 9 9 9 9 9 9 9 . . . . . . . . . . . . . .
    . 4 4 4 f 8 6 6 6 6 6 6 9 9 9 9 9 6 6 6 . . . . . . . . . . . .
    4 4 4 f 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 . . . . . . . . .
    . 4 4 f 6 8 8 8 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 . . . . . . . .
    . . 4 4 f 8 8 . . . . . 8 8 8 8 6 6 6 6 6 6 6 . . . . . . . . .
    . . . . . . . . . . . 8 8 8 8 8 8 2 . . . . . . . . . . . . . .
    . . . . . . . . . . . 8 8 8 8 8 2 . . . . . . . . . . . . . . .
    . . . . . . . . . . 8 8 8 8 8 2 . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
`, SpriteKind.Player)
raumschiff.setStayInScreen(true)
// @highlight
info.setLife(3)
```

## {Schrit 4}

``||controller:Bewege||`` nun das ``||variables(noclick):Raumschiff||`` mit den ``||controller:Steuerungstasten||`` und ändere die Empfindlichkeit von ``vx`` und ``vy`` auf ``200``.

```typescript
let raumschiff = sprites.create(img`
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . 8 2 . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . 1 1 1 . . . . . 9 9 9 9 9 . . . . . . . . . . . . . . .
    . . . . 2 2 2 2 . . . 9 9 9 9 9 9 9 . . . . . . . . . . . . . .
    . 4 4 4 f 8 6 6 6 6 6 6 9 9 9 9 9 6 6 6 . . . . . . . . . . . .
    4 4 4 f 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 . . . . . . . . .
    . 4 4 f 6 8 8 8 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 . . . . . . . .
    . . 4 4 f 8 8 . . . . . 8 8 8 8 6 6 6 6 6 6 6 . . . . . . . . .
    . . . . . . . . . . . 8 8 8 8 8 8 2 . . . . . . . . . . . . . .
    . . . . . . . . . . . 8 8 8 8 8 2 . . . . . . . . . . . . . . .
    . . . . . . . . . . 8 8 8 8 8 2 . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
`, SpriteKind.Player)
raumschiff.setStayInScreen(true)
info.setLife(3)
// @highlight
controller.moveSprite(raumschiff, 200, 200)
```

## {Schrit 5}

Füge ein Ereignis hinzu, um Code auszuführen, wenn ``||controller:Taste A gedrückt||`` wird. Erstelle in diesem Fall ein ``||sprites:Projektil-Sprite||`` namens Rakete, das ``||sprites:vom||`` ``||variables(noclick):raumschiff||`` aus gestartet wird, und legen Sie die Empfindlichkeit ``vx`` auf ``200`` festund ``vy`` auf ``0``.

```typescript
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    let rakete = sprites.createProjectileFromSprite(img`
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . 5 a a 2 . . . . . . . . .
        . . 5 5 a 2 2 2 2 4 4 4 . . . .
        . . . 5 a a 2 . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
    `, raumschiff, 200, 0)
})
```

## {Schrit 6}

Füge ein weiteres Ereignis hinzu, um jede ``||game:halbe Sekunde Code beim Spielupdate||`` auszuführen. Erstelle in diesem Fall ein ``||sprites:Sprite||`` des typen ``||sprites:Enemy||``(gegner), benenne es gegner,und zeichne das feindliche Flugzeug hinein.

```typescript
game.onUpdateInterval(500, function () {
    let gegner = sprites.create(img`
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . 9 9 . . . . . 5 . . . .
        . . . 9 9 9 9 . . . 5 5 . . . .
        2 2 2 2 9 9 2 2 2 2 2 f 4 4 . .
        . . 2 2 2 2 5 5 5 2 2 f 4 4 4 .
        . . . . . . 5 5 5 . . . . . . .
        . . . . . . . 5 5 . . . . . . .
        . . . . . . . . 5 . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
    `, SpriteKind.Enemy)
})
```

## {Schrit 7}

Stelle beim ``||variables(noclick):gegnerischen Sprite||`` die ``||sprites:Geschwindigkeit||`` mit einem Werten ein, damit es **horizontal** von **rechts nach links** fliegt.

```typescript
game.onUpdateInterval(500, function () {
    let gegner = sprites.create(img`
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . 9 9 . . . . . 5 . . . .
        . . . 9 9 9 9 . . . 5 5 . . . .
        2 2 2 2 9 9 2 2 2 2 2 f 4 4 . .
        . . 2 2 2 2 5 5 5 2 2 f 4 4 4 .
        . . . . . . 5 5 5 . . . . . . .
        . . . . . . . 5 5 . . . . . . .
        . . . . . . . . 5 . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
    `, SpriteKind.Enemy)
    // @highlight
    gegner.setVelocity(-100, 0)
})
```

## {Schrit 8}

Füge Code hinzu, um ``||sprites:links||`` vom ``||variables(noclick):Gegner||` auf die ``||scene:Bildschirmbreite||`` und ``||sprites:y||`` auf eine ``||math:Zufallszahl||`` zwischen 0 und ``||scene:Bildschirmhöhe||`` festzulegen.

```typescript
game.onUpdateInterval(500, function () {
    let gegner = sprites.create(img`
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . 9 9 . . . . . 5 . . . .
        . . . 9 9 9 9 . . . 5 5 . . . .
        2 2 2 2 9 9 2 2 2 2 2 f 4 4 . .
        . . 2 2 2 2 5 5 5 2 2 f 4 4 4 .
        . . . . . . 5 5 5 . . . . . . .
        . . . . . . . 5 5 . . . . . . .
        . . . . . . . . 5 . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
    `, SpriteKind.Enemy)
    gegner.setVelocity(-100, 0)
    // @highlight
    gegner.left = scene.screenWidth()
    // @highlight
    gegner.y = randint(0, scene.screenHeight())
})
```

## {Schrit 9}

Um zu verhindern, dass die Anzahl der ``||sprites:gegnerischen Sprites||` zunimmt, obwohl sie den Bildschirm verlassen, stelle die Flagge für die ``||sprites:automatische Zerstörung||`` des ``||variables(noclick):Gegners||`` auf **EIN**.

```typescript
game.onUpdateInterval(500, function () {
    let gegner = sprites.create(img`
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . 9 9 . . . . . 5 . . . .
        . . . 9 9 9 9 . . . 5 5 . . . .
        2 2 2 2 9 9 2 2 2 2 2 f 4 4 . .
        . . 2 2 2 2 5 5 5 2 2 f 4 4 4 .
        . . . . . . 5 5 5 . . . . . . .
        . . . . . . . 5 5 . . . . . . .
        . . . . . . . . 5 . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
    `, SpriteKind.Enemy)
    gegner.setVelocity(-100, 0)
    gegner.left = scene.screenWidth()
    gegner.y = randint(0, scene.screenHeight())
    // @highlight
    gegner.setFlag(SpriteFlag.AutoDestroy, true)
})
```

