# Geospatial Data Gatekeeper 🛡️
**Automated QA/QC Engine for Spatial Data Governance**

A Python-based tool built with **ArcPy** to automate rigorous quality control for oil and gas spatial data. This tool ensures that every feature class entering the database meets strict organizational standards.

### 🛠️ Key Features (4-Layer Validation)
1. **Naming Convention:** Uses Regex to enforce strict standardized naming.
2. **Geometry Integrity:** Checks for correct geometry types (e.g., Point for Wells).
3. **Spatial Reference:** Ensures all data uses the approved Coordinate Reference System (CRS).
4. **Attribute Schema:** Validates the existence of mandatory fields (UWI, WELL_NAME, etc.).

### ⚡ Performance Benchmarks
* **Execution Time:** 0.11 seconds for 5 SHP files.
* **Scalability:** Optimized to handle 10,000+ records in seconds using `arcpy.da.SearchCursor`.

### 📊 Deliverables
The tool automatically generates a **CSV Audit Report**, providing a clear list of "PASS/FAIL" status and specific error messages for immediate data remediation.

| File Name | Geometry Type | Coordinate System | QC STATUS | Error Notes |
| :--- | :--- | :--- | :--- | :--- |
| CAPTOIL_WELL | Point | GCS_WGS_1984 | **FAIL** | Invalid Naming Format (Required: WK_YEAR_WELLS) |
| PAXMA_2013_WELLS | Point | GCS_WGS_1984 | **FAIL** | Missing Attribute Fields: CLASS |
| PETROLAST_2010_WELLS | Point | GCS_WGS_1984 | **PASS** | Data Clean & Compliant |
| PINPANOIL_2017_WELLS | Point | GCS_WGS_1984 | **FAIL** | Null Data Detected: [Row 1 (OPERATOR is Null/Empty)] |
| SEAGAS_2015_WELLS | Polygon | WGS_1984_UTM_Zone_52S | **FAIL** | Invalid Geometry (Required: Point, Actual: Polygon) |

![Automated Audit Report](detailed-qc-report)
*Figure 1: Sample of the CSV Audit Report showing real-time validation logs and error detection.*
