# Electrostatics — Point Charges & Electric Fields

An interactive browser simulation of Coulomb's law, electric field superposition, and the force on a test charge. Built for high-school and introductory university physics.

## How to Open

Open `index.html` in any modern browser. No server, no installation.

---

## Physics Covered

| Formula | What it models |
|---|---|
| `F = kq₁q₂/r²` | Coulomb force between two point charges |
| `E = kq/r²` | Electric field magnitude from a single charge |
| `E⃗_total = Σ E⃗ᵢ` | Superposition: total field = vector sum of all contributions |
| `F⃗_test = q_t · E⃗_total` | Force on a test charge in the combined field |

**Constant:** k = 8.9875 × 10⁹ N·m²/C²

---

## Canvas Interactions

| Action | Effect |
|---|---|
| Left-click on empty space | Place a new charge (uses current sign & magnitude settings) |
| Left-click on charge | Select it (highlights in yellow; shows info in HUD) |
| Right-click on charge | Delete it |
| Drag a charge | Reposition it; all forces and field update live |
| Drag the test charge | Move the test charge; force arrow updates live |

---

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `R` | Remove all charges and the test charge |
| `Escape` | Cancel adding test charge / deselect |
| `Delete` / `Backspace` | Delete the currently selected charge |

---

## Panel Controls

### Place Charge

| Control | Options | Effect |
|---|---|---|
| Sign | `+` / `−` | Polarity of the next charge placed |
| Magnitude | `1 µC` / `5 µC` / `10 µC` | Size (absolute value) of charge; ball radius scales accordingly |
| Clear All | button | Removes every placed charge |

### Display

| Control | Default | Effect |
|---|---|---|
| Force arrows on charges | ON | Orange arrow on each charge showing net Coulomb force from all others |
| Electric field grid | ON | Grid of arrows showing E⃗ direction and relative magnitude everywhere |
| Colour by \|E\| magnitude | OFF | Heat-map colouring: blue (weak) → cyan → green → yellow → red (strong) |
| Grid density | Medium | Slider: Coarse (16×11) / Medium (22×15) / Fine (32×22) grid points |

### Test Charge

| Control | Detail |
|---|---|
| Add Test Charge | Enters placement mode; next canvas click drops the test charge |
| `1 C (unit)` | Sets q_t = 1 C — the force arrow then numerically equals the field vector |
| `Custom` | Reveals a log-scale slider: 1 nC → 100 µC |
| Remove Test Charge | Removes the green test charge |

---

## Display Modes Explained

### Force arrows on charges
Each placed charge shows an orange arrow representing the **vector sum of Coulomb forces** from all other placed charges. Arrow length is log-scaled so both weak and strong forces are visible. The label shows the magnitude (e.g. `F = 1.34 mN`).

Only displayed when ≥ 2 charges are present.

### Electric field grid
A regular grid of small arrows is drawn over the canvas. Each arrow:
- Points in the direction of **E⃗_total** at that grid point
- Has length proportional to **log₁₀(|E|)**, clamped so faint fields still show
- Is skipped near charge positions (singularities are excluded within ~0.35 m)

Toggle **Colour by |E|** to apply a heat-map: blue = weak field, red = strong field.

### Test charge
A green circle labelled `qₜ`. Its force arrow (green) shows **F⃗ = q_t · E⃗_total** at its position.

Use `1 C` mode to make the force arrow identical to the field arrow — a common high-school demonstration that **1 C is the SI unit test charge**.

---

## Physics Notes

### Coulomb's Law
```
F = k · |q₁| · |q₂| / r²
```
Direction: repulsive for like signs, attractive for opposite signs.

### Superposition Principle
The total electric field at any point is the **vector sum** of contributions from every charge:
```
E⃗_total(r⃗) = Σᵢ  k·qᵢ / |r⃗ − r⃗ᵢ|²  ·  (r⃗ − r⃗ᵢ) / |r⃗ − r⃗ᵢ|
```

### Test Charge Convention
The test charge is treated as a **passive observer** — it does not exert forces on the placed charges. This is the standard high-school convention: q_t is assumed small enough that it does not disturb the source field.

### Units & Scale
- World space: ±3.2 m in each axis
- Charges: µC range (realistic for classroom demonstrations)
- Forces: displayed in N, mN, µN, nN as appropriate

---

## File Structure

```
electrostatics/
├── index.html    ← complete self-contained simulation
└── README.md
```
