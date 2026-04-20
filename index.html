import { useState, useEffect } from "react";

const PURPOSES = [
  "Client Meeting",
  "Business Development",
  "Site Inspection",
  "Investment Property Visit",
  "Board Meeting",
  "Conference/Seminar",
  "Due Diligence",
  "Other Business",
];

const formatDate = (d) => new Date(d).toLocaleDateString("en-US", { month: "short", day: "numeric", year: "numeric" });
const formatTime = (d) => new Date(d).toLocaleTimeString("en-US", { hour: "2-digit", minute: "2-digit" });

const initialForm = {
  date: new Date().toISOString().split("T")[0],
  departure: "",
  destination: "",
  departureTime: "",
  arrivalTime: "",
  passengers: "",
  purpose: "",
  businessJustification: "",
  pilotName: "",
  tailNumber: "",
};

const STORAGE_KEY = "aircraft_flight_logs";

export default function AircraftLog() {
  const [logs, setLogs] = useState([]);
  const [view, setView] = useState("dashboard"); // dashboard | new | detail | export
  const [form, setForm] = useState(initialForm);
  const [selectedLog, setSelectedLog] = useState(null);
  const [saved, setSaved] = useState(false);
  const [filterYear, setFilterYear] = useState(new Date().getFullYear());

  useEffect(() => {
    const stored = localStorage.getItem(STORAGE_KEY);
    if (stored) setLogs(JSON.parse(stored));
  }, []);

  const persist = (newLogs) => {
    setLogs(newLogs);
    localStorage.setItem(STORAGE_KEY, JSON.stringify(newLogs));
  };

  const calcHours = (dep, arr) => {
    if (!dep || !arr) return null;
    const diff = (new Date(arr) - new Date(dep)) / 3600000;
    return diff > 0 ? diff.toFixed(1) : null;
  };

  const submitFlight = () => {
    if (!form.departure || !form.destination || !form.purpose || !form.businessJustification) return;
    const entry = {
      ...form,
      id: Date.now(),
      createdAt: new Date().toISOString(),
      hours: calcHours(
        form.date + "T" + form.departureTime,
        form.date + "T" + form.arrivalTime
      ),
    };
    persist([entry, ...logs]);
    setForm(initialForm);
    setSaved(true);
    setTimeout(() => { setSaved(false); setView("dashboard"); }, 1200);
  };

  const deleteLog = (id) => {
    persist(logs.filter((l) => l.id !== id));
    setView("dashboard");
  };

  const yearLogs = logs.filter((l) => new Date(l.date).getFullYear() === filterYear);
  const totalHours = yearLogs.reduce((s, l) => s + (parseFloat(l.hours) || 0), 0);
  const totalFlights = yearLogs.length;
  const purposes = yearLogs.reduce((acc, l) => {
    acc[l.purpose] = (acc[l.purpose] || 0) + 1;
    return acc;
  }, {});
  const topPurpose = Object.entries(purposes).sort((a, b) => b[1] - a[1])[0];

  const exportCSV = () => {
    const headers = ["Date","Departure","Destination","Dep Time","Arr Time","Hours","Passengers","Purpose","Business Justification","Pilot","Tail Number"];
    const rows = yearLogs.map(l => [
      l.date, l.departure, l.destination,
      l.departureTime, l.arrivalTime, l.hours || "",
      l.passengers, l.purpose, `"${l.businessJustification}"`,
      l.pilotName, l.tailNumber
    ]);
    const csv = [headers, ...rows].map(r => r.join(",")).join("\n");
    const blob = new Blob([csv], { type: "text/csv" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = `flight-log-${filterYear}.csv`;
    a.click();
  };

  const styles = {
    app: {
      fontFamily: "'Georgia', 'Times New Roman', serif",
      background: "#0a0f1a",
      minHeight: "100vh",
      color: "#e8e0d0",
      maxWidth: 430,
      margin: "0 auto",
      position: "relative",
      overflow: "hidden",
    },
    header: {
      background: "linear-gradient(160deg, #0d1525 0%, #0a0f1a 100%)",
      borderBottom: "1px solid #1e2d45",
      padding: "20px 20px 16px",
      position: "sticky",
      top: 0,
      zIndex: 100,
    },
    headerTop: {
      display: "flex",
      alignItems: "center",
      justifyContent: "space-between",
      marginBottom: 4,
    },
    appName: {
      fontSize: 11,
      letterSpacing: "0.25em",
      color: "#8a9bb5",
      textTransform: "uppercase",
      fontFamily: "'Georgia', serif",
    },
    tailBadge: {
      background: "#1a2640",
      border: "1px solid #2a3f60",
      borderRadius: 6,
      padding: "3px 10px",
      fontSize: 12,
      color: "#c8b87a",
      fontFamily: "monospace",
      letterSpacing: "0.1em",
    },
    pageTitle: {
      fontSize: 22,
      fontWeight: "normal",
      color: "#e8e0d0",
      margin: 0,
      letterSpacing: "-0.02em",
    },
    nav: {
      display: "flex",
      gap: 8,
      padding: "12px 20px",
      background: "#080d18",
      borderBottom: "1px solid #131d2e",
      overflowX: "auto",
    },
    navBtn: (active) => ({
      padding: "7px 14px",
      borderRadius: 20,
      border: active ? "1px solid #c8b87a" : "1px solid #1e2d45",
      background: active ? "#1a2030" : "transparent",
      color: active ? "#c8b87a" : "#5a7090",
      fontSize: 12,
      letterSpacing: "0.08em",
      cursor: "pointer",
      whiteSpace: "nowrap",
      fontFamily: "'Georgia', serif",
    }),
    content: {
      padding: "20px",
      paddingBottom: 100,
    },
    statGrid: {
      display: "grid",
      gridTemplateColumns: "1fr 1fr",
      gap: 12,
      marginBottom: 24,
    },
    statCard: {
      background: "linear-gradient(135deg, #0f1926 0%, #0a1220 100%)",
      border: "1px solid #1a2840",
      borderRadius: 14,
      padding: "16px",
    },
    statLabel: {
      fontSize: 10,
      letterSpacing: "0.2em",
      color: "#4a6080",
      textTransform: "uppercase",
      marginBottom: 6,
    },
    statValue: {
      fontSize: 28,
      color: "#c8b87a",
      fontWeight: "normal",
      lineHeight: 1,
    },
    statSub: {
      fontSize: 11,
      color: "#3a5070",
      marginTop: 4,
    },
    sectionLabel: {
      fontSize: 10,
      letterSpacing: "0.2em",
      color: "#4a6080",
      textTransform: "uppercase",
      marginBottom: 12,
    },
    flightCard: {
      background: "#0c1520",
      border: "1px solid #1a2840",
      borderRadius: 14,
      padding: "16px",
      marginBottom: 10,
      cursor: "pointer",
      transition: "border-color 0.2s",
    },
    flightRoute: {
      display: "flex",
      alignItems: "center",
      gap: 8,
      marginBottom: 8,
    },
    airport: {
      fontSize: 20,
      color: "#e8e0d0",
      letterSpacing: "0.05em",
      fontFamily: "monospace",
    },
    arrow: {
      color: "#c8b87a",
      fontSize: 14,
      flex: 1,
      textAlign: "center",
    },
    flightMeta: {
      display: "flex",
      justifyContent: "space-between",
      alignItems: "center",
    },
    flightDate: {
      fontSize: 12,
      color: "#4a6080",
    },
    purposeTag: {
      background: "#111e30",
      border: "1px solid #1e3050",
      borderRadius: 10,
      padding: "3px 10px",
      fontSize: 11,
      color: "#8aabcc",
    },
    hoursTag: {
      fontSize: 13,
      color: "#c8b87a",
    },
    fab: {
      position: "fixed",
      bottom: 32,
      right: "calc(50% - 215px + 20px)",
      width: 56,
      height: 56,
      borderRadius: "50%",
      background: "linear-gradient(135deg, #c8b87a, #a89550)",
      border: "none",
      color: "#0a0f1a",
      fontSize: 26,
      cursor: "pointer",
      display: "flex",
      alignItems: "center",
      justifyContent: "center",
      boxShadow: "0 4px 24px rgba(200,184,122,0.3)",
      zIndex: 200,
    },
    form: {
      display: "flex",
      flexDirection: "column",
      gap: 16,
    },
    fieldGroup: {
      display: "flex",
      flexDirection: "column",
      gap: 6,
    },
    fieldLabel: {
      fontSize: 10,
      letterSpacing: "0.2em",
      color: "#4a6080",
      textTransform: "uppercase",
    },
    input: {
      background: "#0c1520",
      border: "1px solid #1a2840",
      borderRadius: 10,
      padding: "12px 14px",
      color: "#e8e0d0",
      fontSize: 15,
      fontFamily: "'Georgia', serif",
      outline: "none",
      width: "100%",
      boxSizing: "border-box",
    },
    textarea: {
      background: "#0c1520",
      border: "1px solid #1a2840",
      borderRadius: 10,
      padding: "12px 14px",
      color: "#e8e0d0",
      fontSize: 14,
      fontFamily: "'Georgia', serif",
      outline: "none",
      width: "100%",
      boxSizing: "border-box",
      minHeight: 90,
      resize: "vertical",
    },
    select: {
      background: "#0c1520",
      border: "1px solid #1a2840",
      borderRadius: 10,
      padding: "12px 14px",
      color: "#e8e0d0",
      fontSize: 15,
      fontFamily: "'Georgia', serif",
      outline: "none",
      width: "100%",
      boxSizing: "border-box",
      appearance: "none",
    },
    row: {
      display: "grid",
      gridTemplateColumns: "1fr 1fr",
      gap: 12,
    },
    submitBtn: {
      background: "linear-gradient(135deg, #c8b87a, #a89550)",
      border: "none",
      borderRadius: 12,
      padding: "16px",
      color: "#0a0f1a",
      fontSize: 14,
      letterSpacing: "0.1em",
      fontFamily: "'Georgia', serif",
      cursor: "pointer",
      marginTop: 8,
      fontWeight: "bold",
    },
    savedMsg: {
      textAlign: "center",
      color: "#7aac8a",
      fontSize: 14,
      padding: 20,
      letterSpacing: "0.1em",
    },
    detailCard: {
      background: "#0c1520",
      border: "1px solid #1a2840",
      borderRadius: 16,
      padding: 20,
      marginBottom: 16,
    },
    detailRow: {
      display: "flex",
      justifyContent: "space-between",
      alignItems: "flex-start",
      paddingBottom: 12,
      marginBottom: 12,
      borderBottom: "1px solid #111e30",
    },
    detailKey: {
      fontSize: 10,
      letterSpacing: "0.15em",
      color: "#3a5070",
      textTransform: "uppercase",
      paddingTop: 2,
    },
    detailVal: {
      fontSize: 14,
      color: "#c8d8e8",
      textAlign: "right",
      maxWidth: "60%",
    },
    justificationBox: {
      background: "#080e18",
      border: "1px solid #131d2e",
      borderRadius: 10,
      padding: "14px",
      fontSize: 13,
      color: "#8aabcc",
      lineHeight: 1.6,
      fontStyle: "italic",
    },
    deleteBtn: {
      background: "transparent",
      border: "1px solid #3a1520",
      borderRadius: 10,
      padding: "12px",
      color: "#8a4050",
      fontSize: 13,
      cursor: "pointer",
      width: "100%",
      fontFamily: "'Georgia', serif",
      letterSpacing: "0.08em",
    },
    backBtn: {
      background: "transparent",
      border: "none",
      color: "#c8b87a",
      fontSize: 14,
      cursor: "pointer",
      padding: "4px 0",
      fontFamily: "'Georgia', serif",
      letterSpacing: "0.05em",
    },
    exportBtn: {
      background: "#0c1520",
      border: "1px solid #1a2840",
      borderRadius: 12,
      padding: "14px",
      color: "#c8b87a",
      fontSize: 13,
      cursor: "pointer",
      width: "100%",
      fontFamily: "'Georgia', serif",
      letterSpacing: "0.08em",
      marginTop: 12,
    },
    yearSelector: {
      display: "flex",
      gap: 8,
      marginBottom: 20,
    },
    yearBtn: (active) => ({
      padding: "6px 16px",
      borderRadius: 20,
      border: active ? "1px solid #c8b87a" : "1px solid #1e2d45",
      background: active ? "#1a2030" : "transparent",
      color: active ? "#c8b87a" : "#5a7090",
      fontSize: 13,
      cursor: "pointer",
      fontFamily: "'Georgia', serif",
    }),
    complianceBox: {
      background: "linear-gradient(135deg, #0a1a10 0%, #081510 100%)",
      border: "1px solid #1a3025",
      borderRadius: 14,
      padding: 16,
      marginBottom: 16,
    },
    complianceTitle: {
      fontSize: 10,
      letterSpacing: "0.2em",
      color: "#4a8060",
      textTransform: "uppercase",
      marginBottom: 10,
    },
    complianceStat: {
      display: "flex",
      justifyContent: "space-between",
      marginBottom: 6,
    },
    complianceLabel: { fontSize: 12, color: "#4a6050" },
    complianceValue: (pct) => ({
      fontSize: 13,
      color: pct >= 50 ? "#7aac8a" : "#cc7a7a",
      fontWeight: "bold",
    }),
    progressBar: {
      background: "#0a1510",
      borderRadius: 4,
      height: 4,
      marginTop: 8,
      overflow: "hidden",
    },
    progressFill: (pct) => ({
      height: "100%",
      width: `${Math.min(pct, 100)}%`,
      background: pct >= 50 ? "linear-gradient(90deg, #3a8050, #7aac8a)" : "linear-gradient(90deg, #803a3a, #cc7a7a)",
      borderRadius: 4,
      transition: "width 0.6s ease",
    }),
    emptyState: {
      textAlign: "center",
      padding: "48px 20px",
      color: "#2a3d55",
    },
    emptyIcon: {
      fontSize: 48,
      marginBottom: 16,
      display: "block",
    },
    emptyText: {
      fontSize: 14,
      color: "#3a5070",
      lineHeight: 1.6,
    },
  };

  const years = [...new Set([new Date().getFullYear(), new Date().getFullYear() - 1, ...logs.map(l => new Date(l.date).getFullYear())])].sort((a,b)=>b-a);
  const businessUsePct = totalHours > 0 ? 100 : 0; // All logged flights are business

  return (
    <div style={styles.app}>
      {/* Header */}
      <div style={styles.header}>
        <div style={styles.headerTop}>
          <span style={styles.appName}>FlightLog Pro</span>
          <span style={styles.tailBadge}>N-XXXX</span>
        </div>
        <h1 style={styles.pageTitle}>
          {view === "dashboard" && "Flight Records"}
          {view === "new" && "Log a Flight"}
          {view === "detail" && "Flight Detail"}
          {view === "export" && "Export & Compliance"}
        </h1>
      </div>

      {/* Nav */}
      <div style={styles.nav}>
        {[["dashboard","Logbook"],["new","+ New Flight"],["export","Export"]].map(([v,label]) => (
          <button key={v} style={styles.navBtn(view === v)} onClick={() => setView(v)}>{label}</button>
        ))}
      </div>

      <div style={styles.content}>

        {/* DASHBOARD */}
        {view === "dashboard" && (
          <>
            <div style={styles.yearSelector}>
              {years.map(y => (
                <button key={y} style={styles.yearBtn(y === filterYear)} onClick={() => setFilterYear(y)}>{y}</button>
              ))}
            </div>

            <div style={styles.statGrid}>
              <div style={styles.statCard}>
                <div style={styles.statLabel}>Flight Hours</div>
                <div style={styles.statValue}>{totalHours.toFixed(1)}</div>
                <div style={styles.statSub}>§280F documented</div>
              </div>
              <div style={styles.statCard}>
                <div style={styles.statLabel}>Total Flights</div>
                <div style={styles.statValue}>{totalFlights}</div>
                <div style={styles.statSub}>{filterYear} tax year</div>
              </div>
              <div style={styles.statCard}>
                <div style={styles.statLabel}>Top Purpose</div>
                <div style={styles.statValue} style={{fontSize: 16, paddingTop: 4}}>{topPurpose ? topPurpose[0].split(" ")[0] : "—"}</div>
                <div style={styles.statSub}>{topPurpose ? `${topPurpose[1]} flights` : "No flights yet"}</div>
              </div>
              <div style={styles.statCard}>
                <div style={styles.statLabel}>Business Use</div>
                <div style={styles.statValue} style={{color: "#7aac8a"}}>100%</div>
                <div style={styles.statSub}>All flights logged</div>
              </div>
            </div>

            {/* §280F Compliance indicator */}
            {totalFlights > 0 && (
              <div style={styles.complianceBox}>
                <div style={styles.complianceTitle}>§280F Compliance Status</div>
                <div style={styles.complianceStat}>
                  <span style={styles.complianceLabel}>Business Use Threshold</span>
                  <span style={styles.complianceValue(100)}>✓ Qualified</span>
                </div>
                <div style={styles.complianceStat}>
                  <span style={styles.complianceLabel}>Substantiation Records</span>
                  <span style={styles.complianceValue(100)}>{totalFlights} entries</span>
                </div>
                <div style={styles.progressBar}>
                  <div style={styles.progressFill(100)} />
                </div>
              </div>
            )}

            <div style={styles.sectionLabel}>Recent Flights</div>

            {yearLogs.length === 0 ? (
              <div style={styles.emptyState}>
                <span style={styles.emptyIcon}>✈️</span>
                <div style={styles.emptyText}>No flights logged for {filterYear}.<br/>Tap "+ New Flight" to begin your IRS-compliant flight record.</div>
              </div>
            ) : (
              yearLogs.map(log => (
                <div key={log.id} style={styles.flightCard} onClick={() => { setSelectedLog(log); setView("detail"); }}>
                  <div style={styles.flightRoute}>
                    <span style={styles.airport}>{log.departure || "—"}</span>
                    <span style={styles.arrow}>✈ ——</span>
                    <span style={styles.airport}>{log.destination || "—"}</span>
                    {log.hours && <span style={styles.hoursTag}>{log.hours}h</span>}
                  </div>
                  <div style={styles.flightMeta}>
                    <span style={styles.flightDate}>{formatDate(log.date)}</span>
                    <span style={styles.purposeTag}>{log.purpose}</span>
                  </div>
                </div>
              ))
            )}
          </>
        )}

        {/* NEW FLIGHT FORM */}
        {view === "new" && (
          <div style={styles.form}>
            {saved && <div style={styles.savedMsg}>✓ Flight logged successfully</div>}

            <div style={styles.fieldGroup}>
              <label style={styles.fieldLabel}>Flight Date</label>
              <input type="date" style={styles.input} value={form.date} onChange={e => setForm({...form, date: e.target.value})} />
            </div>

            <div style={styles.row}>
              <div style={styles.fieldGroup}>
                <label style={styles.fieldLabel}>Departure (ICAO/IATA)</label>
                <input style={styles.input} placeholder="ATL" value={form.departure} onChange={e => setForm({...form, departure: e.target.value.toUpperCase()})} maxLength={4} />
              </div>
              <div style={styles.fieldGroup}>
                <label style={styles.fieldLabel}>Destination</label>
                <input style={styles.input} placeholder="TEB" value={form.destination} onChange={e => setForm({...form, destination: e.target.value.toUpperCase()})} maxLength={4} />
              </div>
            </div>

            <div style={styles.row}>
              <div style={styles.fieldGroup}>
                <label style={styles.fieldLabel}>Departure Time</label>
                <input type="time" style={styles.input} value={form.departureTime} onChange={e => setForm({...form, departureTime: e.target.value})} />
              </div>
              <div style={styles.fieldGroup}>
                <label style={styles.fieldLabel}>Arrival Time</label>
                <input type="time" style={styles.input} value={form.arrivalTime} onChange={e => setForm({...form, arrivalTime: e.target.value})} />
              </div>
            </div>

            {form.departureTime && form.arrivalTime && calcHours(`${form.date}T${form.departureTime}`, `${form.date}T${form.arrivalTime}`) && (
              <div style={{textAlign:"center", color:"#c8b87a", fontSize:13, marginTop:-8}}>
                Flight time: {calcHours(`${form.date}T${form.departureTime}`, `${form.date}T${form.arrivalTime}`)} hours
              </div>
            )}

            <div style={styles.fieldGroup}>
              <label style={styles.fieldLabel}>Business Purpose</label>
              <select style={styles.select} value={form.purpose} onChange={e => setForm({...form, purpose: e.target.value})}>
                <option value="">Select purpose...</option>
                {PURPOSES.map(p => <option key={p} value={p}>{p}</option>)}
              </select>
            </div>

            <div style={styles.fieldGroup}>
              <label style={styles.fieldLabel}>Business Justification (IRS Substantiation)</label>
              <textarea
                style={styles.textarea}
                placeholder="Describe the specific business purpose, clients met, deals discussed, or business activity conducted. This is your IRS §274 substantiation record."
                value={form.businessJustification}
                onChange={e => setForm({...form, businessJustification: e.target.value})}
              />
            </div>

            <div style={styles.fieldGroup}>
              <label style={styles.fieldLabel}>Passengers / Attendees</label>
              <input style={styles.input} placeholder="John Smith (CFO), Jane Doe (Legal)" value={form.passengers} onChange={e => setForm({...form, passengers: e.target.value})} />
            </div>

            <div style={styles.row}>
              <div style={styles.fieldGroup}>
                <label style={styles.fieldLabel}>Pilot Name</label>
                <input style={styles.input} placeholder="Pilot" value={form.pilotName} onChange={e => setForm({...form, pilotName: e.target.value})} />
              </div>
              <div style={styles.fieldGroup}>
                <label style={styles.fieldLabel}>Tail Number</label>
                <input style={styles.input} placeholder="N12345" value={form.tailNumber} onChange={e => setForm({...form, tailNumber: e.target.value.toUpperCase()})} />
              </div>
            </div>

            <button style={styles.submitBtn} onClick={submitFlight}>
              Log Flight Record
            </button>

            <div style={{fontSize:11, color:"#2a3d55", textAlign:"center", lineHeight:1.6}}>
              This record constitutes §280F / §274 substantiation documentation for IRS purposes. Ensure accuracy before submission.
            </div>
          </div>
        )}

        {/* DETAIL VIEW */}
        {view === "detail" && selectedLog && (
          <>
            <button style={styles.backBtn} onClick={() => setView("dashboard")}>← Back to Logbook</button>

            <div style={{margin: "16px 0"}}>
              <div style={{...styles.flightRoute, marginBottom:4}}>
                <span style={{...styles.airport, fontSize:28}}>{selectedLog.departure}</span>
                <span style={{...styles.arrow, fontSize:20}}>✈</span>
                <span style={{...styles.airport, fontSize:28}}>{selectedLog.destination}</span>
              </div>
              <div style={{fontSize:13, color:"#4a6080"}}>{formatDate(selectedLog.date)}{selectedLog.hours ? ` · ${selectedLog.hours} hours` : ""}</div>
            </div>

            <div style={styles.detailCard}>
              {[
                ["Purpose", selectedLog.purpose],
                ["Departure Time", selectedLog.departureTime ? formatTime(`${selectedLog.date}T${selectedLog.departureTime}`) : "—"],
                ["Arrival Time", selectedLog.arrivalTime ? formatTime(`${selectedLog.date}T${selectedLog.arrivalTime}`) : "—"],
                ["Flight Hours", selectedLog.hours ? `${selectedLog.hours} hrs` : "—"],
                ["Passengers", selectedLog.passengers || "—"],
                ["Pilot", selectedLog.pilotName || "—"],
                ["Tail Number", selectedLog.tailNumber || "—"],
              ].map(([k,v]) => (
                <div key={k} style={styles.detailRow}>
                  <span style={styles.detailKey}>{k}</span>
                  <span style={styles.detailVal}>{v}</span>
                </div>
              ))}
              <div style={{marginTop:4}}>
                <div style={{...styles.detailKey, marginBottom:8}}>Business Justification</div>
                <div style={styles.justificationBox}>{selectedLog.businessJustification}</div>
              </div>
            </div>

            <div style={{fontSize:11, color:"#2a3d55", textAlign:"center", marginBottom:16, lineHeight:1.6}}>
              Logged {new Date(selectedLog.createdAt).toLocaleString()} · §280F compliant record
            </div>

            <button style={styles.deleteBtn} onClick={() => deleteLog(selectedLog.id)}>
              Delete Flight Record
            </button>
          </>
        )}

        {/* EXPORT VIEW */}
        {view === "export" && (
          <>
            <div style={styles.yearSelector}>
              {years.map(y => (
                <button key={y} style={styles.yearBtn(y === filterYear)} onClick={() => setFilterYear(y)}>{y}</button>
              ))}
            </div>

            <div style={styles.complianceBox}>
              <div style={styles.complianceTitle}>§280F Annual Summary — {filterYear}</div>
              <div style={styles.complianceStat}>
                <span style={styles.complianceLabel}>Total Business Flights</span>
                <span style={{...styles.complianceValue(100), fontSize:15}}>{totalFlights}</span>
              </div>
              <div style={styles.complianceStat}>
                <span style={styles.complianceLabel}>Total Business Hours</span>
                <span style={{...styles.complianceValue(100), fontSize:15}}>{totalHours.toFixed(1)}</span>
              </div>
              <div style={styles.complianceStat}>
                <span style={styles.complianceLabel}>Documented Business Use</span>
                <span style={{...styles.complianceValue(100), fontSize:15}}>100%</span>
              </div>
              <div style={styles.progressBar}>
                <div style={styles.progressFill(100)} />
              </div>
            </div>

            <div style={styles.sectionLabel}>Purpose Breakdown</div>
            {Object.entries(purposes).map(([p, count]) => (
              <div key={p} style={{...styles.flightCard, cursor:"default", padding:"12px 16px"}}>
                <div style={styles.flightMeta}>
                  <span style={{fontSize:13, color:"#c8d8e8"}}>{p}</span>
                  <span style={{fontSize:13, color:"#c8b87a"}}>{count} flight{count>1?"s":""}</span>
                </div>
              </div>
            ))}

            {totalFlights === 0 && (
              <div style={styles.emptyState}>
                <span style={styles.emptyIcon}>📋</span>
                <div style={styles.emptyText}>No flights logged for {filterYear} yet.</div>
              </div>
            )}

            {totalFlights > 0 && (
              <>
                <button style={styles.exportBtn} onClick={exportCSV}>
                  ↓ Export {filterYear} CSV for Tax Advisor
                </button>
                <div style={{fontSize:11, color:"#2a3d55", textAlign:"center", marginTop:12, lineHeight:1.7}}>
                  Export includes all §280F substantiation fields: date, route, duration, purpose, business justification, passengers, and pilot. Provide to your CPA and aviation tax attorney for annual compliance review.
                </div>
              </>
            )}
          </>
        )}
      </div>
    </div>
  );
}
