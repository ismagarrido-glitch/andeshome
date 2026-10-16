<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>P3: Portal ASN & Agenda de Andenes YMS</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- QRCode.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#eef2ff',
                            100: '#e0e7ff',
                            500: '#6366f1',
                            600: '#4f46e5',
                            700: '#4338ca',
                            900: '#312e81',
                        }
                    }
                }
            }
        }
    </script>
    Aquí tienes el archivo completo `index.html`. Está diseñado en un único archivo auto-contenido que incluye la interfaz ejecutiva del proyecto P3 y el portal *mobile-first* ultra-simplificado para conductores (acceso por RUT, escáner QR de garita y pase digital).

### Código HTML Completo (`index.html`)

Copia todo el siguiente bloque de código y guárdalo en un archivo llamado **`index.html`**:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>P3: Portal ASN + YMS Ligero</title>
  
  <!-- Tailwind CSS CDN -->
  <script src="[https://cdn.tailwindcss.com](https://cdn.tailwindcss.com)"></script>
  <!-- Chart.js CDN -->
  <script src="[https://cdn.jsdelivr.net/npm/chart.js](https://cdn.jsdelivr.net/npm/chart.js)"></script>
  <!-- Lucide Icons -->
  <script src="[https://unpkg.com/lucide@latest](https://unpkg.com/lucide@latest)"></script>
  <!-- QR Code Generator Generator library -->
  <script src="[https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js](https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js)"></script>

  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brand: {
              50: '#f0fdf4',
              100: '#dcfce7',
              500: '#22c55e',
              600: '#16a34a',
              700: '#15803d',
              800: '#166534',
              900: '#14532d',
            },
            accent: {
              500: '#0284c7',
              600: '#0369a1',
            }
          }
        }
      }
    }
  </script>
</head>
<body class="bg-slate-50 font-sans text-slate-800 antialiased min-h-screen flex flex-col">

  <!-- HEADER GLOBAL -->
  <header class="bg-slate-900 text-white sticky top-0 z-50 shadow-md">
    <div class="max-w-7xl mx-auto px-4 py-3 flex flex-wrap justify-between items-center gap-4">
      <div class="flex items-center gap-3">
        <div class="bg-brand-500 text-slate-900 font-bold p-2 rounded-lg text-sm flex items-center justify-center">
          P3
        </div>
        <div>
          <h1 class="font-bold text-base md:text-lg leading-tight">Portal ASN + YMS Ligero</h1>
          <p class="text-xs text-slate-400 hidden sm:block">Tecnología & Proceso Logístico Express</p>
        </div>
      </div>

      <!-- Selector de Modo/Vista -->
      <div class="flex items-center bg-slate-800 p-1 rounded-xl border border-slate-700">
        <button id="btn-view-admin" onclick="switchView('admin')" class="px-3 py-1.5 text-xs font-semibold rounded-lg transition-all bg-brand-500 text-slate-950 shadow">
          <i data-lucide="layout-dashboard" class="inline w-3.5 h-3.5 mr-1"></i> Dashboard Proyecto
        </button>
        <button id="btn-view-driver" onclick="switchView('driver')" class="px-3 py-1.5 text-xs font-semibold rounded-lg transition-all text-slate-300 hover:text-white">
          <i data-lucide="smartphone" class="inline w-3.5 h-3.5 mr-1"></i> App Chofer (Express)
        </button>
      </div>
    </div>
  </header>

  <!-- CONTENEDOR PRINCIPAL -->
  <main class="flex-grow max-w-7xl w-full mx-auto px-4 py-6">

    <!-- ==================== VISTA 1: DASHBOARD EJECUTIVO YMS ==================== -->
    <div id="view-admin" class="space-y-8">

      <!-- HERO / BANNER PRINCIPAL -->
      <div class="bg-gradient-to-r from-slate-900 via-slate-800 to-slate-900 rounded-2xl p-6 md:p-8 text-white shadow-xl relative overflow-hidden">
        <div class="relative z-10 max-w-3xl">
          <span class="inline-block bg-brand-500/20 text-brand-500 border border-brand-500/30 font-semibold text-xs px-3 py-1 rounded-full mb-3">
            Iniciativa ID: P3 | Sinergia directa con P2
          </span>
          <h2 class="text-2xl md:text-4xl font-extrabold tracking-tight mb-2">Portal ASN y Agendamiento Ligero</h2>
          <p class="text-slate-300 text-sm md:text-base mb-6">
            Optimización de flujo en patios y andenes mediante digitalización ágil sin fricción para transporte y proveedores.
          </p>

          <!-- Tarjetas KPI -->
          <div class="grid grid-cols-2 md:grid-cols-4 gap-3 md:gap-4">
            <div class="bg-slate-800/80 backdrop-blur p-3 md:p-4 rounded-xl border border-slate-700">
              <p class="text-xs text-slate-400 font-medium">CAPEX (CLP)</p>
              <p class="text-lg md:text-xl font-bold text-white">$95.000.000</p>
            </div>
            <div class="bg-slate-800/80 backdrop-blur p-3 md:p-4 rounded-xl border border-slate-700">
              <p class="text-xs text-slate-400 font-medium">OPEX Anual</p>
              <p class="text-lg md:text-xl font-bold text-white">$24.000.000</p>
            </div>
            <div class="bg-slate-800/80 backdrop-blur p-3 md:p-4 rounded-xl border border-slate-700">
              <p class="text-xs text-slate-400 font-medium">Plazo Estimado</p>
              <p class="text-lg md:text-xl font-bold text-brand-500">14 Semanas</p>
            </div>
            <div class="bg-slate-800/80 backdrop-blur p-3 md:p-4 rounded-xl border border-slate-700">
              <p class="text-xs text-slate-400 font-medium">Nivel de Riesgo</p>
              <p class="text-lg md:text-xl font-bold text-emerald-400">Bajo</p>
            </div>
          </div>
        </div>
      </div>

      <!-- SECCIÓN DE IMPACTO Y GRÁFICOS -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <!-- Gráfico -->
        <div class="lg:col-span-2 bg-white rounded-2xl p-6 shadow-sm border border-slate-200">
          <div class="flex justify-between items-center mb-4">
            <div>
              <h3 class="font-bold text-slate-900 text-lg">Impacto Esperado en Operaciones</h3>
              <p class="text-xs text-slate-500">Comparativa Situación Actual vs Proyectada P3</p>
            </div>
            <span class="bg-emerald-100 text-emerald-800 text-xs px-2.5 py-1 rounded-full font-medium">ROI Alto</span>
          </div>
          <div class="h-64 relative">
            <canvas id="kpiChart"></canvas>
          </div>
        </div>

        <!-- Tarjetas Metas -->
        <div class="space-y-4">
          <div class="bg-white p-5 rounded-2xl border border-slate-200 shadow-sm flex items-center gap-4">
            <div class="p-3 bg-emerald-100 text-emerald-700 rounded-xl">
              <i data-lucide="timer" class="w-6 h-6"></i>
            </div>
            <div>
              <p class="text-2xl font-black text-slate-900">-30%</p>
              <p class="text-xs font-semibold text-slate-600">Dock-to-Stock</p>
              <p class="text-xs text-slate-400">Agiliza la recepción en bodega</p>
            </div>
          </div>

          <div class="bg-white p-5 rounded-2xl border border-slate-200 shadow-sm flex items-center gap-4">
            <div class="p-3 bg-blue-100 text-blue-700 rounded-xl">
              <i data-lucide="truck" class="w-6 h-6"></i>
            </div>
            <div>
              <p class="text-2xl font-black text-slate-900">-40%</p>
              <p class="text-xs font-semibold text-slate-600">Tiempo de Espera</p>
              <p class="text-xs text-slate-400">Reducción de colas en patio/garita</p>
            </div>
          </div>

          <div class="bg-white p-5 rounded-2xl border border-slate-200 shadow-sm flex items-center gap-4">
            <div class="p-3 bg-indigo-100 text-indigo-700 rounded-xl">
              <i data-lucide="calendar-check" class="w-6 h-6"></i>
            </div>
            <div>
              <p class="text-2xl font-black text-slate-900">+15 pp</p>
              <p class="text-xs font-semibold text-slate-600">Cumplimiento Citas</p>
              <p class="text-xs text-slate-400">Mayor exactitud en ventanas horarias</p>
            </div>
          </div>
        </div>
      </div>

      <!-- MONITOR EN TIEMPO REAL / SIMULADOR PATIO DE ANDENES -->
      <div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200">
        <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-6">
          <div>
            <h3 class="font-bold text-slate-900 text-lg flex items-center gap-2">
              <i data-lucide="layout-grid" class="w-5 h-5 text-brand-600"></i>
              Estado de Andenes en Tiempo Real (YMS Ligero)
            </h3>
            <p class="text-xs text-slate-500">Monitor en vivo para jefes de patio y seguridad en garita</p>
          </div>
          <button onclick="generateGaritaQR()" class="inline-flex items-center gap-2 text-xs font-semibold bg-slate-900 text-white px-3 py-2 rounded-lg hover:bg-slate-800 transition">
            <i data-lucide="qr-code" class="w-4 h-4"></i> Generar QR Entrada Garita
          </button>
        </div>

        <!-- Matriz de Andenes -->
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4" id="docks-container">
          <!-- Generado Dinámicamente por JS -->
        </div>

        <!-- Tabla Registro Reciente -->
        <div class="mt-8">
          <h4 class="text-sm font-bold text-slate-800 mb-3 flex items-center gap-2">
            <i data-lucide="list" class="w-4 h-4 text-slate-500"></i> Últimos Ingresos (RUT Express)
          </h4>
          <div class="overflow-x-auto">
            <table class="w-full text-left text-xs">
              <thead class="bg-slate-100 text-slate-600 uppercase font-semibold">
                <tr>
                  <th class="p-3">RUT Conductor</th>
                  <th class="p-3">Área / Centro</th>
                  <th class="p-3">Patente</th>
                  <th class="p-3">Andén</th>
                  <th class="p-3">Estado</th>
                  <th class="p-3">Hora Ingreso</th>
                </tr>
              </thead>
              <tbody id="logs-table-body" class="divide-y divide-slate-100 font-medium text-slate-700">
                <!-- Se llena con JS -->
              </tbody>
            </table>
          </div>
        </div>
      </div>

      <!-- ROADMAP Y CONDICIONES CLAVE -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <!-- Roadmap Semanal -->
        <div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200">
          <h3 class="font-bold text-slate-900 text-base mb-4 flex items-center gap-2">
            <i data-lucide="milestone" class="w-5 h-5 text-accent-600"></i> Roadmap de Implementación (14 Semanas)
          </h3>
          <div class="space-y-3 relative border-l-2 border-slate-200 ml-3 pl-4">
            <div class="relative">
              <span class="absolute -left-[23px] top-1 w-3.5 h-3.5 rounded-full bg-brand-500 border-2 border-white"></span>
              <p class="text-xs font-bold text-slate-900">Sem 1 - 4: Diseño & Integración P2</p>
              <p class="text-xs text-slate-500">Definición de flujo sin fricción, conectores API para RUT y OCs.</p>
            </div>
            <div class="relative">
              <span class="absolute -left-[23px] top-1 w-3.5 h-3.5 rounded-full bg-slate-300 border-2 border-white"></span>
              <p class="text-xs font-bold text-slate-900">Sem 5 - 9: Desarrollo Portal ASN & YMS Ligero</p>
              <p class="text-xs text-slate-500">Módulo de auto-registro por RUT, generación de QR para garita.</p>
            </div>
            <div class="relative">
              <span class="absolute -left-[23px] top-1 w-3.5 h-3.5 rounded-full bg-slate-300 border-2 border-white"></span>
              <p class="text-xs font-bold text-slate-900">Sem 10 - 12: Piloto & Onboarding Proveedores</p>
              <p class="text-xs text-slate-500">Capacitación ultra-corta (SLA) y pruebas en andenes reales.</p>
            </div>
            <div class="relative">
              <span class="absolute -left-[23px] top-1 w-3.5 h-3.5 rounded-full bg-slate-300 border-2 border-white"></span>
              <p class="text-xs font-bold text-slate-900">Sem 13 - 14: Go-Live & Despliegue Total</p>
              <p class="text-xs text-slate-500">Operación 100% activa en Vercel/Cloud sin servidores complejos.</p>
            </div>
          </div>
        </div>

        <!-- Riesgos & Sinergias -->
        <div class="bg-white rounded-2xl p-6 shadow-sm border border-slate-200 flex flex-col justify-between">
          <div>
            <h3 class="font-bold text-slate-900 text-base mb-3 flex items-center gap-2">
              <i data-lucide="shield-alert" class="w-5 h-5 text-amber-500"></i> Riesgos Clave & Mitigación
            </h3>
            <div class="bg-amber-50 border border-amber-200 rounded-xl p-3 mb-4 text-xs text-amber-900">
              <p class="font-bold">Condición Clave: Adopción de Proveedores & SLAs</p>
              <p class="mt-1">Para mitigar resistencia, el acceso no exige crear cuenta previa: solo ingresar RUT/Patente al llegar a garita o vía QR.</p>
            </div>

            <h4 class="font-bold text-slate-900 text-sm mb-2 flex items-center gap-2">
              <i data-lucide="link" class="w-4 h-4 text-brand-600"></i> Sinergia con Proyecto P2
            </h4>
            <p class="text-xs text-slate-600">
              Aprovecha la base de datos de proveedores y órdenes de compra de P2, evitando duplicidad de información y agilizando la trazabilidad.
            </p>
          </div>

          <div class="mt-4 pt-4 border-t border-slate-100 flex items-center justify-between text-xs text-slate-400">
            <span>Despliegue directo en Vercel</span>
            <span class="font-mono bg-slate-100 px-2 py-0.5 rounded text-slate-600">GitHub Ready</span>
          </div>
        </div>
      </div>

    </div>

    <!-- ==================== VISTA 2: APP CONDUCTOR (MOBILE-FIRST) ==================== -->
    <div id="view-driver" class="hidden max-w-md mx-auto">
      
      <div class="bg-white rounded-3xl shadow-xl border border-slate-200 overflow-hidden">
        <!-- Banner App Chofer -->
        <div class="bg-slate-900 p-6 text-white text-center relative">
          <span class="bg-brand-500 text-slate-950 font-extrabold text-[10px] px-2.5 py-0.5 rounded-full uppercase tracking-wider mb-2 inline-block">Acceso Express Conductor</span>
          <h2 class="text-xl font-black">Ingreso a Centro de Distribución</h2>
          <p class="text-xs text-slate-400 mt-1">Sin claves ni registros largos. Solo tu RUT.</p>
        </div>

        <div class="p-6 space-y-5">
          <!-- Formulario Directo -->
          <form id="driver-form" onsubmit="handleDriverRegister(event)" class="space-y-4">
            <div>
              <label class="block text-xs font-bold text-slate-700 uppercase mb-1">1. Tu RUT / DNI</label>
              <div class="relative">
                <input type="text" id="driver-rut" required placeholder="12.345.678-9" class="w-full pl-10 pr-3 py-3 rounded-xl border border-slate-300 focus:ring-2 focus:ring-brand-500 focus:border-brand-500 text-sm font-semibold outline-none transition">
                <i data-lucide="id-card" class="w-5 h-5 text-slate-400 absolute left-3 top-3.5"></i>
              </div>
            </div>

            <div>
              <label class="block text-xs font-bold text-slate-700 uppercase mb-1">2. Patente Camión</label>
              <div class="relative">
                <input type="text" id="driver-plate" required placeholder="ABCD-12" class="w-full pl-10 pr-3 py-3 rounded-xl border border-slate-300 focus:ring-2 focus:ring-brand-500 focus:border-brand-500 text-sm font-semibold uppercase outline-none transition">
                <i data-lucide="truck" class="w-5 h-5 text-slate-400 absolute left-3 top-3.5"></i>
              </div>
            </div>

            <div>
              <label class="block text-xs font-bold text-slate-700 uppercase mb-1">3. Área / Destino de Carga</label>
              <div class="relative">
                <select id="driver-area" required class="w-full pl-10 pr-3 py-3 rounded-xl border border-slate-300 focus:ring-2 focus:ring-brand-500 focus:border-brand-500 text-sm font-semibold outline-none transition bg-white">
                  <option value="">Selecciona el área de trabajo...</option>
                  <option value="CD Central - Recepción Secos">CD Central - Recepción Secos</option>
                  <option value="CD Central - Frío / Refrigerados">CD Central - Frío / Refrigerados</option>
                  <option value="Bodega B - Carga General">Bodega B - Carga General</option>
                  <option value="Devoluciones / Retorno">Devoluciones / Retorno</option>
                </select>
                <i data-lucide="map-pin" class="w-5 h-5 text-slate-400 absolute left-3 top-3.5"></i>
              </div>
            </div>

            <button type="submit" class="w-full bg-brand-600 hover:bg-brand-700 active:scale-98 text-white font-bold py-3.5 rounded-xl shadow-lg shadow-brand-600/30 transition flex items-center justify-center gap-2 text-sm">
              <i data-lucide="check-circle" class="w-5 h-5"></i>
              SOLICITAR ANDÉN Y TICKET
            </button>
          </form>

          <!-- Ticket Digital Generado (Oculto inicialmente) -->
          <div id="driver-ticket" class="hidden bg-slate-50 rounded-2xl p-5 border-2 border-brand-500/30 text-center space-y-4">
            <div class="inline-flex p-2 bg-emerald-100 text-emerald-800 rounded-full">
              <i data-lucide="check-check" class="w-6 h-6"></i>
            </div>
            <div>
              <span class="text-[10px] uppercase tracking-wider font-bold text-emerald-700 bg-emerald-100 px-2.5 py-0.5 rounded-full">
                ¡Ingreso Registrado!
              </span>
              <h3 class="text-xl font-black text-slate-900 mt-2" id="ticket-dock-assigned">Andén # --</h3>
              <p class="text-xs text-slate-500" id="ticket-info">RUT: -- | Patente: --</p>
            </div>

            <div class="bg-white p-3 rounded-xl shadow-inner inline-block mx-auto border border-slate-200">
              <div id="qrcode-ticket" class="flex justify-center"></div>
              <p class="text-[10px] text-slate-400 mt-2 font-mono">Presenta este código en Garita</p>
            </div>

            <button onclick="resetDriverForm()" class="text-xs font-semibold text-slate-500 underline block mx-auto">
              Registrar otro ingreso
            </button>
          </div>
        </div>
      </div>

    </div>

  </main>

  <!-- MODAL QR GARITA -->
  <div id="modal-qr" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm hidden z-50 flex items-center justify-center p-4">
    <div class="bg-white rounded-3xl p-6 max-w-sm w-full text-center space-y-4 shadow-2xl">
      <h3 class="font-bold text-slate-900 text-lg">QR de Acceso para Garita</h3>
      <p class="text-xs text-slate-500">Imprime este código y colócalo en la entrada. Los choferes lo escanearán para registrarse en 10 segundos.</p>
      
      <div class="bg-slate-50 p-4 rounded-2xl border border-slate-200 flex justify-center">
        <div id="garita-qr-container"></div>
      </div>

      <div class="flex gap-2">
        <button onclick="closeModalQR()" class="w-full py-2.5 bg-slate-200 text-slate-800 font-bold text-xs rounded-xl hover:bg-slate-300 transition">
          Cerrar
        </button>
      </div>
    </div>
  </div>

  <!-- JAVASCRIPT LÓGICA -->
  <script>
    // Inicialización de Iconos Lucide
    lucide.createIcons();

    // Estado Global de Andenes
    const docks = [
      { id: 'Andén 01', status: 'ocupado', rut: '15.420.119-K', patente: 'HX-9021', area: 'CD Central - Recepción Secos', time: '10:15' },
      { id: 'Andén 02', status: 'libre', rut: '', patente: '', area: '', time: '' },
      { id: 'Andén 03', status: 'ocupado', rut: '9.812.330-4', patente: 'CP-4412', area: 'CD Central - Frío', time: '10:40' },
      { id: 'Andén 04', status: 'libre', rut: '', patente: '', area: '', time: '' }
    ];

    // Cambiar entre Vistas
    function switchView(view) {
      const adminView = document.getElementById('view-admin');
      const driverView = document.getElementById('view-driver');
      const btnAdmin = document.getElementById('btn-view-admin');
      const btnDriver = document.getElementById('btn-view-driver');

      if (view === 'admin') {
        adminView.classList.remove('hidden');
        driverView.classList.add('hidden');
        btnAdmin.className = "px-3 py-1.5 text-xs font-semibold rounded-lg transition-all bg-brand-500 text-slate-950 shadow";
        btnDriver.className = "px-3 py-1.5 text-xs font-semibold rounded-lg transition-all text-slate-300 hover:text-white";
      } else {
        adminView.classList.add('hidden');
        driverView.classList.remove('hidden');
        btnDriver.className = "px-3 py-1.5 text-xs font-semibold rounded-lg transition-all bg-brand-500 text-slate-950 shadow";
        btnAdmin.className = "px-3 py-1.5 text-xs font-semibold rounded-lg transition-all text-slate-300 hover:text-white";
      }
    }

    // Renderizar Andenes
    function renderDocks() {
      const container = document.getElementById('docks-container');
      const tableBody = document.getElementById('logs-table-body');
      container.innerHTML = '';
      tableBody.innerHTML = '';

      docks.forEach((dock, index) => {
        const isFree = dock.status === 'libre';
        
        // Tarjetas de Andén
        const dockCard = document.createElement('div');
        dockCard.className = `p-4 rounded-xl border-2 transition ${
          isFree 
            ? 'bg-emerald-50/50 border-emerald-300/60 text-emerald-950' 
            : 'bg-slate-50 border-slate-300 text-slate-800'
        }`;

        dockCard.innerHTML = `
          <div class="flex justify-between items-center mb-2">
            <span class="font-extrabold text-sm">${dock.id}</span>
            <span class="text-[10px] font-bold uppercase px-2 py-0.5 rounded-full ${
              isFree ? 'bg-emerald-200 text-emerald-800' : 'bg-slate-200 text-slate-700'
            }">
              ${dock.status}
            </span>
          </div>
          <div class="text-xs space-y-1 my-3">
            <p><span class="text-slate-400">RUT:</span> ${dock.rut || '---'}</p>
            <p><span class="text-slate-400">Patente:</span> ${dock.patente || '---'}</p>
          </div>
          <button onclick="toggleDock(${index})" class="w-full text-xs font-bold py-1.5 rounded-lg transition ${
            isFree 
              ? 'bg-emerald-600 hover:bg-emerald-700 text-white' 
              : 'bg-slate-200 hover:bg-slate-300 text-slate-700'
          }">
            ${isFree ? 'Asignar Manual' : 'Liberar Andén'}
          </button>
        `;
        container.appendChild(dockCard);

        // Fila de Tabla
        if (!isFree) {
          const row = document.createElement('tr');
          row.innerHTML = `
            <td class="p-3 font-semibold">${dock.rut}</td>
            <td class="p-3">${dock.area}</td>
            <td class="p-3 uppercase">${dock.patente}</td>
            <td class="p-3 font-bold text-brand-700">${dock.id}</td>
            <td class="p-3"><span class="bg-blue-100 text-blue-800 px-2 py-0.5 rounded text-[10px] font-bold">En Descarga</span></td>
            <td class="p-3 text-slate-400">${dock.time} hrs</td>
          `;
          tableBody.appendChild(row);
        }
      });
    }

    // Alternar estado de andén
    function toggleDock(index) {
      if (docks[index].status === 'libre') {
        docks[index].status = 'ocupado';
        docks[index].rut = '12.345.678-9';
        docks[index].patente = 'EXPRESS-1';
        docks[index].area = 'CD Central - Recepción Secos';
        docks[index].time = new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
      } else {
        docks[index].status = 'libre';
        docks[index].rut = '';
        docks[index].patente = '';
        docks[index].area = '';
        docks[index].time = '';
      }
      renderDocks();
    }

    // Registro desde Vista Conductor
    function handleDriverRegister(event) {
      event.preventDefault();
      const rut = document.getElementById('driver-rut').value;
      const plate = document.getElementById('driver-plate').value;
      const area = document.getElementById('driver-area').value;

      // Buscar primer andén libre
      const freeDockIndex = docks.findIndex(d => d.status === 'libre');

      let assignedDockName = 'En Espera (Patio)';
      if (freeDockIndex !== -1) {
        docks[freeDockIndex].status = 'ocupado';
        docks[freeDockIndex].rut = rut;
        docks[freeDockIndex].patente = plate;
        docks[freeDockIndex].area = area;
        docks[freeDockIndex].time = new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
        assignedDockName = docks[freeDockIndex].id;
        renderDocks();
      }

      // Ocultar Form, Mostrar Ticket
      document.getElementById('driver-form').classList.add('hidden');
      const ticket = document.getElementById('driver-ticket');
      ticket.classList.remove('hidden');

      document.getElementById('ticket-dock-assigned').innerText = assignedDockName;
      document.getElementById('ticket-info').innerText = `RUT: ${rut} | Patente: ${plate.toUpperCase()}`;

      // Generar QR para el Ticket
      const qrContainer = document.getElementById('qrcode-ticket');
      qrContainer.innerHTML = '';
      new QRCode(qrContainer, {
        text: `TICKET-${rut}-${plate}`,
        width: 120,
        height: 120
      });
    }

    function resetDriverForm() {
      document.getElementById('driver-form').reset();
      document.getElementById('driver-form').classList.remove('hidden');
      document.getElementById('driver-ticket').classList.add('hidden');
    }

    // Generar QR Garita Modal
    function generateGaritaQR() {
      const modal = document.getElementById('modal-qr');
      const container = document.getElementById('garita-qr-container');
      container.innerHTML = '';
      
      new QRCode(container, {
        text: window.location.href,
        width: 160,
        height: 160
      });

      modal.classList.remove('hidden');
    }

    function closeModalQR() {
      document.getElementById('modal-qr').classList.add('hidden');
    }

    // Inicialización de Gráfico KPI
    window.onload = function() {
      renderDocks();

      const ctx = document.getElementById('kpiChart').getContext('2d');
      new Chart(ctx, {
        type: 'bar',
        data: {
          labels: ['Dock-to-Stock (min)', 'Tiempo Espera (min)', 'Cumplimiento Citas (%)'],
          datasets: [
            {
              label: 'Situación Actual',
              data: [90, 60, 70],
              backgroundColor: '#cbd5e1',
              borderRadius: 6
            },
            {
              label: 'Proyectado Proyecto P3',
              data: [63, 36, 85],
              backgroundColor: '#22c55e',
              borderRadius: 6
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          plugins: {
            legend: { position: 'bottom' }
          },
          scales: {
            y: { beginAtZero: true }
          }
        }
      });
    };
  </script>
</body>
</html>
