```java
package age.of.civilizations2.jakowski.lukasz;

class CFG() {

    protected static void loadFontMain() {
        if (CFG.fontMain != null) {
            CFG.fontMain.dispose();
            CFG.fontMain = null;
        }
        String sFont = langManager.get("font");
        if (sFont.equals("font")) {
            sFont = "rbold.ttf";
        }
        CFG.loadedRobotoFont = sFont.equals("rbold.ttf");
        FreeTypeFontGenerator generator;
        try {
            generator = new FreeTypeFontGenerator(Gdx.files.internal("game/fonts/" + sFont));
        } catch (GdxRuntimeException ex) {
            generator = new FreeTypeFontGenerator(Gdx.files.internal("game/fonts/rbold.ttf"));
        }
        FreeTypeFontGenerator.FreeTypeFontParameter params = new FreeTypeFontGenerator.FreeTypeFontParameter();
        params.size = Math.max(settingsManager.FONT_MAIN_SIZE, 6);
        params.color = Color.WHITE;
        params.minFilter = Texture.TextureFilter.Linear;
        params.magFilter = Texture.TextureFilter.Linear;
        params.incremental = true;
        CFG.fontMain = generator.generateFont(params);
        CFG.glyphLayout.setText(fontMain, "Ay");
        CFG.TEXT_HEIGHT = (int) glyphLayout.height;
        CFG.settingsManager.updateCitiesFontScale();
    }
}
```
