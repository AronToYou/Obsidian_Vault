# Rhein-Nadel Automation GmbH
> [!NOTE]- History
> - in 2016 gegründet?

| Produkt                   | digitaler Zwilling     |
| ------------------------- | ---------------------- |
| Bedienoberfläche          | Qt                     |
| Physik-/Kontaktsimulation | AGX Dynamics (Algoryx) |
| 3D-Darstellung            | OpenGL + GLSL Shaders  |
- Simulieren / Analysieren / Optimieren
	- **Optimieren**:
		- Model/View-Performance
		- Caching
		- Async-Jobs
		- saubere Threading-Grenzen
			- UI-Thread vs. Simulation/Render-Thread
## Dein Profil
- Du verfügst über hervorragende Coding-Skills in C++/Qt.
	- Dabei spielt es für uns eine untergeordnete Rolle, ob diese im Studium, in der Ausbildung oder autodidaktisch erworben wurden.
- Du hast idealerweise den Softwareentwicklungsprozess 
	- vom UI/UX Design bis hin zum Go-Live begleitet
	- und hast daher Kenntnisse im Code-Review, Test und Release-Management.
- Idealerweise interessiert du dich für Simulation, digitale Zwillinge und High-Tech-Maschinenbau
- Folgende Toolkenntnisse sind zwingend erforderlich
	- C++
	- Qt
	- OpenGL
	- GLSL-Shader
	- Git/GitHub
---
# Erfahrung
- habe schon mit digitalem Zwilling gearbeitet

## Bedienoberfläche
- habe auch UI-Bausteine gebaut:
	- Parameter-Panels
	- Property-Editoren
	- Tabellen / Baumansichte für
		- Anlagen
		- Verbindungen (mit SPS-Geräten)

## Physiksimulation
- fire simulation

## 3D-Darstellung
- Graphics rendering class
- Computation Geometry Class
- fire simulation rendering

## Fehlen
- CAD-Dateien
- Schwingverhalten
- Zuführtechnik
# Fragen
- GLSL werden oft nicht „für hübsch“ genutzt, sondern um Information sichtbar zu machen
	- Wann sollte man GLSL statt OpenGL nutzen?
		- Heatmaps
		- Outlines
		- Teifen-Cueing
		- SSAO-light
		- Kontaktpunkte / Kollisionszonen
		- Gelenke, Kräftevektoren
- What is a basic application of `QOpenGLWidget` / `QOpenGLWindow`
- im Interview
	- Welche Render-Architektur? (OpenGL „raw“; Qt3D; oder Qt Quick + custom renderer)
	- Welche Daten kommen rein? (CAD (STEP/IDES); eigene Mesh-Formate; vereinfachte Collision-Shapes)
	- Was wird visualisiert? (Nur Geometrie + Animation; Kontaktkräfte/Heatmaps/Debug-Draw)
	- Wie läuft die Simulation? (Echtzeit interaktiv vs Batch-Runs; headless/offscreen; Cloud-Jobs)
	- Welche AGX-Module/Features? (Kontakte/Reibung; Constraints; Kabel/Drähte; granular material)
# Notes
- die UX hängt in solchen Tools stark davon ab,
	- wie schnell man Varianten durchspielen kann:
		- viele Parameter
		- viele Runs
		- schnelle Vergleichbarkeit
- eingebettetes 3D-Viewport in der Qt-Anwendung
	- `QOpenGLWidget`/`QOpenGLWindow`
	- Qt-Quick-Bridges
	- Example App
		- Navigation
			- Orbit
			- Pan
			- Zoom
			- Selektieren von Teilen
		- Zeichnen
			- Meshes (Bauteile)
			- Linien (Trajektorien)
			- Gizmos?/Koordinatenachsen
		- Rendering-Pipeline
			- Vertex-/Index-Buffers
			- Instancing
			- Culling
			- Depth
			- Transparenzen
# OpenGL / GLSL
## Rasterization Pipeline
- Application
	- input
		- vertices in 3D space
- Vertex Processing
	- vertex stream
		- vertices positioned in screen space
- Triangle Processing
	- triangle stream
		- triangles positioned in screen space
- Rasterization
	- fragment stream
		- fragments (one per covered sample)
- Fragment Processing
	- shaded fragments
- Framebuffer Operations
	- display
		- image (pixels)
## Shader Programs
- triangle processing
	- vertex shaders
	- geometry shaders
- fragment processing
	- fragment shader
		- once per fragment
```cpp
uniform sampler2D myTexture;  // program parameter
uniform vec3 lightDir;        // program parameter
varying vec2 uv;      // per fragment value (inter. by rasterizer)
varying vec3 norm;

void diffuseShader()
{
	vec3 kd;
	kd = texture2d(myTexture, uv);  // material color from texture
	kd *= clamp(dot(-lightDir, norm), 0.0, 1.0);  // Lambertian shading model
	gl_FragColor = vec4(kd, 1.0);  // output fragment color
}
```
# Qt (cute)
- Tree of `QWidget` or QML items
	- widgets inherit `QObject`
		- which have parent/child
- Widgets expose properties
	- edit in Qt Designer / Creator <-> GEDI
```cpp
class Worker : public QObject {
	Q_OBJECT
	public slots:
		void doWork(int x) { /* ... */ }
		
	signals:
		void progress(int p);
};
/* Connect / Emit */
Worker w;
QObject::connect(&w, &Worker::progress, [](int p){ qDebug() << p; });
emit w.progress(42);
/* Reflection / Introspection */
const QMetaObject* mo = w.metaObject();
qDebug() << mo->className();
for (int i=0; i<mo->methodCount(); i++)
{
	QMetaMethod mm = mo->method(i);
	qDebug() << mm.methodSignature();
}
/* Dynamic Properties */
w.setProperty("role", "archiver");  // Stored as QVariant internally
qDebug() << w.property("role").toString();
```
- woboq writup
- panel events callbacks
	- widget`.clicked()`
	- connect/emit signal -> run slot/lambda
	- prefer signal/slots for app logic
- Qt app centered around **event loop**
	- `QApplication` / `QCoreApplication`
- QSS


# EMail
- [ ] `Desktop\CS184`
- [ ] Qt Designer / Creator
- Experience with
	- C++
		- Berkeley
			- Foundations of Graphics Rendering
			- Operating Systems & System Programming
			- Computational Geometry
		- Hardware programming
			- DAC for waveform generation
			- Digital sequencer
	- Qt
		- WinCC OA
			- Panels - QML / Top-level Qt window or container widget
			- object - widget
			- GEDI property - widget property
			- Event Manager - Qt application event loop (and/or threaded worker loops)
			- Panel Events - signal / slot, lambda
			- dpConnect - signals / slots or bindings
		- QSS / CSS

# Qt AlmondBread

- why `setDepthBufferSize` when `glDisable(GL_DEPTH_TEST)`
- why `static const char* kVert = R"GLSL()GLSL"`
- no VBO but still VAO because of core profile
- Why 2 `private:` under `class MandelbrotWidget`
- `#pragma once`