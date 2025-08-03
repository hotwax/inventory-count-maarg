# Inventory Count Maarg

This repository is a Moqui-based component that enables inventory counting features in the Maarg application.

---

# Setup Instructions for `inventory-count-maarg` in development environment

## ✅ Prerequisites

Ensure the following software is installed on your system:

- **Java**: Version 11  
- **MySQL**: Version 8 (any 8.x minor version is supported)

---

## 📦 Code Checkout & Setup

Follow the steps below to set up your local development environment.

### 1. Clone Moqui Framework and Runtime

```bash
git clone -b "main" https://github.com/hotwax/moqui-framework.git cycle-count-maarg
```
```bash
cd cycle-count-maarg
git clone -b "main" https://github.com/hotwax/moqui-runtime.git runtime
````

### 2. Clone Required Components

Navigate to the component directory:

```bash
cd runtime/component
```

Then clone the following repositories:

```bash
git clone -b "main" https://github.com/hotwax/moqui-sftp.git
git clone -b "main" https://github.com/hotwax/moqui-fop.git
git clone -b "main" https://git.hotwax.co/HC2/maarg-docker-config.git
git clone -b "main" https://git.hotwax.co/HC2/plugins/maarg-util.git
git clone -b "main" https://github.com/hotwax/ofbiz-oms-udm.git
git clone -b "main" https://git.hotwax.co/HC2/plugins/ofbiz-oms-usl.git
git clone -b "main" https://github.com/hotwax/inventory-count-maarg.git
```

---

## 🗄️ Create MySQL Schema

Before running Moqui, create a MySQL schema using the proper character set and collation:

```sql
CREATE SCHEMA ofbiz CHARACTER SET utf8 COLLATE utf8_general_ci;
```

> ⚠️ Do **not** use MySQL Workbench defaults unless you verify they match `utf8` and `utf8_general_ci`.

This ensures compatibility with Moqui’s entity model and prevents character encoding or index size issues.

---

## ⚙️ Configure MySQL Connection

You’ll need:

* MySQL database name → `dbname`
* MySQL username → `dbusername`
* MySQL password → `dbpassword`

Open the file:

```
runtime/component/ofbiz-oms-usl/MoquiConf.xml
```

Add or edit the following properties:

```xml
<default-property name="entity_ds_db_conf" value="mysql8"/>
<default-property name="entity_ds_database" value="dbname"/>
<default-property name="entity_ds_user" value="dbusername"/>
<default-property name="entity_ds_password" value="dbpassword"/>
```

---

## 🧪 Load Data

Run the following command from the `moqui-framework` root directory:

```bash
./gradlew load
```

This will load all required data into your MySQL database.

---
