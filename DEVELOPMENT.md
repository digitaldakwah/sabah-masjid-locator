# Sabah Masjid Locator - VS Code Development Setup

## Project Overview
Sabah Masjid Locator is a custom Nextcloud app based on the Maps app, specifically designed for the Islamic community in Sabah, Malaysia. This app provides comprehensive mosque location services and Qiblat direction functionality.

## Development Environment Setup

### Prerequisites
- PHP 8.1+ with required extensions (exif, curl, gd)
- Node.js 18+ and npm
- Nextcloud 30+ development environment
- VS Code with recommended extensions

### Getting Started

1. **Open Workspace**
   ```bash
   code sabah-masjid-locator.code-workspace
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Development Build**
   ```bash
   npm run dev
   ```

4. **Watch Mode (for active development)**
   ```bash
   npm run watch
   ```

### VS Code Tasks Available

- **Install Dependencies**: `Ctrl+Shift+P` → `Tasks: Run Task` → `Install Dependencies`
- **Build Development**: Quick build for testing
- **Build Production**: Optimized build for deployment
- **Watch Development**: Auto-rebuild on file changes
- **Lint JavaScript**: Code quality checks
- **Lint CSS**: Style checks
- **Package App**: Create deployment archive

### Key Development Areas

#### 1. App Configuration
- `appinfo/info.xml` - Main app metadata and configuration
- `package.json` - Node.js dependencies and scripts

#### 2. Backend (PHP)
- `lib/Controller/` - API endpoints and business logic
- `lib/Service/` - Core services (Masjid data, Qiblat calculations)
- `lib/Migration/` - Database setup and Sabah mosque data import

#### 3. Frontend (Vue.js + JavaScript)
- `src/` - Vue.js components and JavaScript modules
- `css/` - Styling and Islamic theme customizations
- `img/` - Icons and graphics (mosque markers, compass)

#### 4. Islamic Features
- Qiblat direction calculations for Sabah coordinates
- Prayer time calculations using Islamic methods
- Sabah mosque database with facilities information
- Arabic/Malay language support

### Sabah-Specific Customizations

#### Default Masjid Locations (Priority Testing Areas)
1. **Kota Kinabalu**: State Mosque, City Mosque, Likas Mosque
2. **Sandakan**: Central Mosque, Masjid Jamek
3. **Tawau**: Main Mosque, Tawau Central Mosque
4. **Lahad Datu**: District Mosque, Community mosques

#### Prayer Time Configuration
- Timezone: Asia/Kuching (UTC+8)
- Calculation Method: JAKIM (Malaysia)
- Latitude range: 4°N to 7°N (Sabah coverage)
- Longitude range: 115°E to 119°E (Sabah coverage)

### Debugging

#### PHP Debugging
- XDebug configuration included for VS Code
- Set breakpoints in PHP files and use "Listen for XDebug"

#### JavaScript Debugging
- Chrome debugging configuration included
- Launch Chrome debugger for frontend testing

### Deployment

#### Development Deployment
```bash
# Build and copy to Nextcloud apps directory
npm run build
sudo cp -r . /var/www/nextcloud/apps/sabah_masjid_locator/
sudo chown -R www-data:www-data /var/www/nextcloud/apps/sabah_masjid_locator/
```

#### Enable App
```bash
sudo -u www-data php /var/www/nextcloud/occ app:enable sabah_masjid_locator
```

### Git Workflow

#### Repository Setup
```bash
git remote add origin https://github.com/digitaldakwah/sabah-masjid-locator.git
git branch -M main
git push -u origin main
```

#### Development Branches
- `main` - Production ready code
- `develop` - Integration branch
- `feature/sabah-mosques` - Sabah mosque database
- `feature/qiblat-compass` - Qiblat direction features
- `feature/prayer-times` - Prayer time integration

### Testing Areas

#### Functional Testing
1. Mosque location display and accuracy
2. Qiblat direction calculation verification
3. Prayer time accuracy for Sabah locations
4. Mobile responsiveness
5. Arabic/Malay text rendering

#### Integration Testing
1. Nextcloud user authentication
2. File sharing with mosque photos
3. User favorites and custom mosque additions
4. Search and filtering functionality

### Support Resources

- [Nextcloud App Development](https://docs.nextcloud.com/server/latest/developer_manual/)
- [Vue.js Documentation](https://vuejs.org/guide/)
- [OpenStreetMap API](https://wiki.openstreetmap.org/wiki/API)
- [Islamic Prayer Time Calculations](https://praytimes.org/manual)

### Contact
- Project Lead: Digital Dakwah Platform Team
- Repository: https://github.com/digitaldakwah/sabah-masjid-locator
- Issues: https://github.com/digitaldakwah/sabah-masjid-locator/issues