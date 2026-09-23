# Industrial Facility Commissioning Checklist

A practical, field-tested checklist for commissioning industrial automation systems — from pre-installation through handover. Based on real experience commissioning large-scale facilities with Siemens PLC/SCADA systems.

> Use this as a starting point. Adapt to your facility type, applicable standards (IEC 62061, ISO 13849), and customer requirements.

---

## Phases

- [Phase 1 — Pre-Commissioning](#phase-1--pre-commissioning)
- [Phase 2 — Electrical & Panel Checks](#phase-2--electrical--panel-checks)
- [Phase 3 — PLC & I/O Verification](#phase-3--plc--io-verification)
- [Phase 4 — HMI / SCADA](#phase-4--hmi--scada)
- [Phase 5 — Network & Communication](#phase-5--network--communication)
- [Phase 6 — Functional Testing](#phase-6--functional-testing)
- [Phase 7 — Safety Systems](#phase-7--safety-systems)
- [Phase 8 — Handover & Documentation](#phase-8--handover--documentation)

---

## Phase 1 — Pre-Commissioning

### Documentation
- [ ] P&ID drawings reviewed and approved (latest revision)
- [ ] Electrical schematics available and match physical installation
- [ ] PLC I/O list verified against drawings
- [ ] Network topology diagram available
- [ ] Equipment datasheets and manuals on site
- [ ] Software backup of PLC program and HMI project stored off-site

### Site Readiness
- [ ] All mechanical installation complete
- [ ] Panel earthing/grounding installed and tested (< 1 Ω)
- [ ] Cable tray installation complete, cables labeled
- [ ] Control room ready (power, cooling, network)
- [ ] Field instruments installed and calibrated (certificates available)

---

## Phase 2 — Electrical & Panel Checks

### Power Supply
- [ ] Incoming supply voltage verified (phase, neutral, earth)
- [ ] UPS tested: bypass, battery backup duration, alarm outputs
- [ ] 24 VDC power supplies loaded and output voltage within spec
- [ ] Panel lighting and socket outlets functional

### Wiring
- [ ] All terminal connections checked (no loose strands, correct torque)
- [ ] Cable screens terminated correctly (one end only unless specified)
- [ ] Fuse ratings verified against load calculations
- [ ] Emergency stop loop continuity confirmed
- [ ] All cable labels match drawing numbers

### Insulation
- [ ] Insulation resistance test completed on all power cables (> 1 MΩ)
- [ ] Test results documented and signed off

---

## Phase 3 — PLC & I/O Verification

### Hardware
- [ ] PLC rack configuration matches hardware catalog in TIA Portal / STEP 7
- [ ] All modules seated correctly, no diagnostic LEDs in fault state
- [ ] Firmware versions documented and compatible
- [ ] CPU memory utilization within acceptable limits (< 80%)

### Digital Inputs (DI)
- [ ] Each DI forced from field device and confirmed in PLC tag table
- [ ] Input filter times set appropriately for signal type
- [ ] Inverted inputs documented and logic verified

### Digital Outputs (DO)
- [ ] Each DO toggled from PLC and verified at field device
- [ ] Output load within relay/transistor ratings
- [ ] Interlock logic prevents simultaneous conflicting outputs

### Analog Inputs (AI)
- [ ] Each AI calibrated: 4 mA = 0%, 20 mA = 100% (or configured range)
- [ ] Broken wire detection enabled and tested
- [ ] Engineering units conversion verified in PLC

### Analog Outputs (AO)
- [ ] Each AO set to known value and confirmed at actuator
- [ ] Fail-safe output state defined and tested (power loss, CPU fault)

### High-Speed / Special Modules
- [ ] Encoder/counter modules: pulse counts verified, rollover handled
- [ ] PID loops: tuning parameters set, auto/manual transfer bump-less

---

## Phase 4 — HMI / SCADA

### Tag Connections
- [ ] All HMI tags connected to correct PLC addresses
- [ ] Read-only tags cannot be written from HMI
- [ ] Tag update rate appropriate for process (fast loops: 100ms, slow: 1s)

### Screens
- [ ] Navigation between all screens functional
- [ ] Process values display in correct engineering units with correct decimal places
- [ ] Setpoint entry limits enforced (min/max validation)
- [ ] All control buttons (start/stop/reset) operate correctly

### Alarms
- [ ] All alarms visible in alarm list with correct priority and description
- [ ] Alarm acknowledge and reset functions tested
- [ ] Alarm history logging to database confirmed
- [ ] Alarm suppression during startup/shutdown modes tested

### Trending
- [ ] All critical process variables configured for trending
- [ ] Historical data retention period meets customer requirement
- [ ] Trend export function tested

---

## Phase 5 — Network & Communication

### Infrastructure
- [ ] All Ethernet switches configured (VLANs, port security if required)
- [ ] IP address scheme documented, no conflicts
- [ ] Firewall rules reviewed — OT network isolated from IT/internet

### PLC Communication
- [ ] PLC to HMI: connection stable, no communication errors in diagnostics
- [ ] PLC to PLC (if applicable): data exchange verified both directions
- [ ] Remote I/O / distributed rack communication: no bus errors

### Industrial Protocols
- [ ] Modbus TCP/RTU devices: all nodes responding, register mapping verified
- [ ] PROFIBUS/PROFINET: all stations online, GSD/GSDML files loaded
- [ ] OPC-UA server (if present): client can browse and read all required nodes
- [ ] MQTT gateway (if present): telemetry data reaching broker

---

## Phase 6 — Functional Testing

### Sequence of Operations
- [ ] Auto start sequence tested step by step against functional spec
- [ ] Auto stop sequence tested (normal and emergency)
- [ ] Manual mode: each actuator controllable independently
- [ ] Mode transitions (manual → auto → manual) smooth, no unexpected trips

### Interlocks
- [ ] Each interlock tested by simulating the fault condition
- [ ] Interlock bypass (if provided): key-switch operated, logged, alarm generated
- [ ] Permissive logic verified: equipment cannot start without all permissives met

### Process Simulation
- [ ] Full process walkthrough with operator: normal production cycle
- [ ] Upset conditions tested (low flow, high temperature, etc.)
- [ ] Recovery from trips tested: operator can restart without engineer intervention

---

## Phase 7 — Safety Systems

> This phase must comply with applicable functional safety standards (IEC 62061 / ISO 13849). Independent verification by a qualified safety engineer may be required.

### Safety PLC / Safety Relay
- [ ] Safety function list reviewed and signed off
- [ ] Each safety function tested: input fault → output de-energized within required response time
- [ ] Proof test interval and diagnostic coverage documented
- [ ] Safety integrity level (SIL/PLr) achieved and verified

### Emergency Stop
- [ ] All E-stop buttons tested: machine comes to safe state within defined time
- [ ] E-stop reset requires deliberate operator action (not automatic)
- [ ] E-stop loop monitoring (OSSD) confirmed functional

### Guards and Interlocks
- [ ] All safety door switches tested: opening guard stops hazardous motion
- [ ] Light curtains / laser scanners: mute function tested (if applicable)

---

## Phase 8 — Handover & Documentation

### As-Built Documentation
- [ ] Drawings updated to reflect as-installed state (red-lined or digital)
- [ ] I/O list updated with any field changes
- [ ] Network diagram updated
- [ ] PLC program: final version backed up, version number recorded
- [ ] HMI project: final version backed up

### Operator Training
- [ ] Operators trained on normal startup and shutdown
- [ ] Operators trained on alarm response and fault recovery
- [ ] Training records signed and filed

### Handover Pack
- [ ] All equipment manuals handed over to customer
- [ ] Spare parts list provided
- [ ] Maintenance schedule provided
- [ ] Support contact information provided
- [ ] Warranty start date recorded

### Sign-Off
- [ ] Customer witness test completed and signed
- [ ] Punch list items resolved or scheduled
- [ ] Handover certificate signed by customer and commissioning engineer

---

## Tips from the Field

**PLC Program Version Control**
Always tag your PLC program with the commissioning date and site name in the program header. Keep at least 3 backup generations: before-commissioning, at-handover, after-first-month.

**Analog Loop Calibration**
Do not trust factory calibration. Always do a live loop check from the transmitter to the PLC with a calibrated mA source. A 0.5 mA offset at 4 mA baseline causes 3% zero error across the full range.

**Interlock Documentation**
Document every interlock bypass you make during commissioning and ensure it is removed before handover. Create a bypass log with reason and timestamp.

**Night-Before-Startup Checklist**
- Is the PLC program the correct version (not a test version)?
- Are all output enable switches in the correct position?
- Is the UPS fully charged?
- Do the operators know who to call if something goes wrong?

---

## Contributing

Contributions welcome — especially checklists for specific industries (food & beverage, water treatment, oil & gas) or specific platforms (Rockwell, Beckhoff, Mitsubishi).

---

## License

MIT — use freely, adapt to your needs.
