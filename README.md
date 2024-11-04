<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema ERP y WMS Avanzado</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/luxon@2.0.2/build/global/luxon.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/sortablejs@1.14.0/Sortable.min.js"></script>
</head>
<body class="bg-gray-100">
    <div class="flex h-screen bg-gray-100">
        <!-- Sidebar -->
        <aside class="w-64 bg-white shadow-md">
            <div class="p-4">
                <h1 class="text-2xl font-bold text-gray-800">Werp</h1>
            </div>
            <nav class="mt-4">
                <a href="#dashboard" class="flex items-center px-4 py-2 text-gray-700 bg-gray-200" onclick="setActiveTab('dashboard')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path></svg>
                    Dashboard
                </a>
                <a href="#inventory" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('inventory')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20 13V6a2 2 0 00-2-2H6a2 2 0 00-2 2v7m16 0v5a2 2 0 01-2 2H6a2 2 0 01-2-2v-5m16 0h-2.586a1 1 0 00-.707.293l-2.414 2.414a1 1 0 01-.707.293h-3.172a1 1 0 01-.707-.293l-2.414-2.414A1 1 0 006.586 13H4"></path></svg>
                    Inventario
                </a>
                <a href="#customers" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('customers')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"></path></svg>
                    Clientes
                </a>
                <a href="#suppliers" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('suppliers')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"></path></svg>
                    Proveedores
                </a>
                <a href="#orders" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('orders')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg>
                    Pedidos
                </a>
                <a href="#purchases" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('purchases')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"></path></svg>
                    Compras
                </a>
                <a href="#warehouse" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('warehouse')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 14v3m4-3v3m4-3v3M3 21h18M3 10h18M3 7l9-4 9 4M4 10h16v11H4V10z"></path></svg>
                    Almacén
                </a>
                <a href="#reports" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('reports')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 17v-2m3 2v-4m3 4v-6m2 10H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path></svg>
                    Informes
                </a>
                <a href="#hr" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('hr')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"></path></svg>
                    Recursos Humanos
                </a>
                <a href="#finance" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('finance')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                    Finanzas
                </a>
                <a href="#settings" class="flex items-center px-4 py-2 text-gray-700" onclick="setActiveTab('settings')">
                    <svg class="w-5 h-5 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                    Configuración
                </a>
            </nav>
        </aside>

        <!-- Main Content -->
        <main class="flex-1 overflow-x-hidden overflow-y-auto bg-gray-100">
            <div class="container mx-auto px-6 py-8">
                <div class="flex items-center justify-between mb-4">
                    <h3 class="text-gray-700 text-3xl font-medium" id="sectionTitle">Dashboard</h3>
                    <div class="flex items-center">
                        <div class="relative">
                            <input class="bg-gray-200 text-gray-700 focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal" type="text" placeholder="Buscar...">
                            <div class="absolute top-0 right-0 mt-2 mr-4">
                                <svg class="h-6 w-6 text-gray-500" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor"><path d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                            </div>
                        </div>
                        <button class="ml-4 bg-gray-200 text-gray-700 py-2 px-4  rounded-lg" onclick="showNotifications()">
                            <svg class="h-6 w-6" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor"><path d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"></path></svg>
                        </button>
                        <button class="ml-4 bg-gray-200 text-gray-700 py-2 px-4 rounded-lg" onclick="showHelp()">
                            <svg class="h-6 w-6" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor"><path d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                        </button>
                    </div>
                </div>

                <!-- Dashboard Content -->
                <div id="dashboardContent" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-8">
                    <div class="bg-white shadow-md rounded-lg p-6">
                        <h4 class="text-lg font-semibold mb-4">Resumen de Ventas</h4>
                        <canvas id="salesChart"></canvas>
                    </div>
                    <div class="bg-white shadow-md rounded-lg p-6">
                        <h4 class="text-lg font-semibold mb-4">Productos Más Vendidos</h4>
                        <canvas id="topProductsChart"></canvas>
                    </div>
                    <div class="bg-white shadow-md rounded-lg p-6">
                        <h4 class="text-lg font-semibold mb-4">KPIs</h4>
                        <div class="space-y-4">
                            <div>
                                <div class="flex justify-between mb-1">
                                    <span>Ventas Mensuales</span>
                                    <span id="monthlySalesKPI">75%</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-2.5">
                                    <div class="bg-blue-600 h-2.5 rounded-full" style="width: 75%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between mb-1">
                                    <span>Satisfacción del Cliente</span>
                                    <span id="customerSatisfactionKPI">90%</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-2.5">
                                    <div class="bg-green-600 h-2.5 rounded-full" style="width: 90%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between mb-1">
                                    <span>Eficiencia del Almacén</span>
                                    <span id="warehouseEfficiencyKPI">60%</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-2.5">
                                    <div class="bg-yellow-600 h-2.5 rounded-full" style="width: 60%"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="bg-white shadow-md rounded-lg p-6">
                        <h4 class="text-lg font-semibold mb-4">Alertas Recientes</h4>
                        <ul id="recentAlerts" class="space-y-2">
                            <!-- Alerts will be dynamically added here -->
                        </ul>
                    </div>
                    <div class="bg-white shadow-md rounded-lg p-6">
                        <h4 class="text-lg font-semibold mb-4">Tareas Pendientes</h4>
                        <ul id="pendingTasks" class="space-y-2">
                            <!-- Tasks will be dynamically added here -->
                        </ul>
                    </div>
                    <div class="bg-white shadow-md rounded-lg p-6">
                        <h4 class="text-lg font-semibold mb-4">Rendimiento de Empleados</h4>
                        <canvas id="employeePerformanceChart"></canvas>
                    </div>
                </div>

                <!-- Inventory Content -->
                <div id="inventoryContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Gestión de Inventario</h4>
                    <div class="mb-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                        <input type="text" id="productName" placeholder="Nombre del producto" class="w-full p-2 border rounded">
                        <input type="number" id="productQuantity" placeholder="Cantidad" class="w-full p-2 border rounded">
                        <input type="number" id="productPrice" placeholder="Precio" class="w-full p-2 border rounded">
                        <input type="text" id="productCategory" placeholder="Categoría" class="w-full p-2 border rounded">
                        <input type="text" id="productSupplier" placeholder="Proveedor" class="w-full p-2 border rounded">
                        <input type="text" id="productLocation" placeholder="Ubicación" class="w-full p-2 border rounded">
                        <input type="number" id="productMinStock" placeholder="Stock Mínimo" class="w-full p-2 border rounded">
                        <input type="number" id="productMaxStock" placeholder="Stock Máximo" class="w-full p-2 border rounded">
                        <input type="text" id="productSKU" placeholder="SKU" class="w-full p-2 border rounded">
                        <button onclick="addProduct()" class="bg-blue-500 text-white p-2 rounded">Añadir Producto</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="min-w-full bg-white">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Nombre</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Cantidad</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Precio</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Categoría</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Proveedor</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Ubicación</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="productTableBody">
                                <!-- Product rows will be added here dynamically -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Customers Content -->
                <div id="customersContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Gestión de Clientes</h4>
                    <div class="mb-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                        <input type="text" id="customerName" placeholder="Nombre del cliente" class="w-full p-2 border rounded">
                        <input type="email" id="customerEmail" placeholder="Email del cliente" class="w-full p-2 border rounded">
                        <input type="tel" id="customerPhone" placeholder="Teléfono del cliente" class="w-full p-2 border rounded">
                        <input type="text" id="customerAddress" placeholder="Dirección del cliente" class="w-full p-2 border rounded">
                        <select id="customerType" class="w-full p-2 border rounded">
                            <option value="">Tipo de cliente</option>
                            <option value="regular">Regular</option>
                            <option value="vip">VIP</option>
                            <option value="corporate">Corporativo</option>
                        </select>
                        <input type="number" id="customerCreditLimit" placeholder="Límite de crédito" class="w-full p-2 border rounded">
                        <button onclick="addCustomer()" class="bg-blue-500 text-white p-2 rounded">Añadir Cliente</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="min-w-full bg-white">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Nombre</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Email</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Teléfono</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Tipo</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Límite de Crédito</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="customerTableBody">
                                <!-- Customer rows will be added here dynamically -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Suppliers Content -->
                <div id="suppliersContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Gestión de Proveedores</h4>
                    <div class="mb-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                        <input type="text" id="supplierName" placeholder="Nombre del proveedor" class="w-full p-2 border rounded">
                        <input type="email" id="supplierEmail" placeholder="Email del proveedor" class="w-full p-2 border rounded">
                        <input type="tel" id="supplierPhone" placeholder="Teléfono del proveedor" class="w-full p-2 border rounded">
                        <input type="text" id="supplierAddress" placeholder="Dirección del proveedor" class="w-full p-2 border rounded">
                        <input type="text" id="supplierProduct" placeholder="Producto principal" class="w-full p-2 border rounded">
                        <input type="number" id="supplierLeadTime" placeholder="Tiempo de entrega (días)" class="w-full p-2 border rounded">
                        <button onclick="addSupplier()" class="bg-blue-500 text-white p-2 rounded">Añadir Proveedor</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="min-w-full bg-white">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Nombre</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Email</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Teléfono</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Producto Principal</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Tiempo de Entrega</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="supplierTableBody">
                                <!-- Supplier rows will be added here dynamically -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Orders Content -->
                <div id="ordersContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Gestión de Pedidos</h4>
                    <div class="mb-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                        <select id="orderCustomer" class="w-full p-2 border rounded">
                            <option value="">Seleccionar Cliente</option>
                            <!-- Customer options will be added dynamically -->
                        </select>
                        <input type="date" id="orderDate" class="w-full p-2 border rounded">
                        <select id="orderStatus" class="w-full p-2 border rounded">
                            <option value="">Estado del Pedido</option>
                            <option value="pending">Pendiente</option>
                            <option value="processing">En Proceso</option>
                            <option value="shipped">Enviado</option>
                            <option value="delivered">Entregado</option>
                        </select>
                        <div id="orderItems" class="col-span-3">
                            <!-- Order items will be added here dynamically -->
                        </div>
                        <button onclick="addOrderItem()" class="bg-green-500 text-white p-2 rounded">Añadir Producto</button>
                        <button onclick="addOrder()" class="bg-blue-500 text-white p-2 rounded">Crear Pedido</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="min-w-full bg-white">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">ID</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Cliente</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Fecha</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Estado</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Total</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="orderTableBody">
                                <!-- Order rows will be added here dynamically -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Purchases Content -->
                <div id="purchasesContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Gestión de Compras</h4>
                    <div class="mb-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                        <select id="purchaseSupplier" class="w-full p-2 border rounded">
                            <option value="">Seleccionar Proveedor</option>
                            <!-- Supplier options will be added dynamically -->
                        </select>
                        <input type="date" id="purchaseDate" class="w-full p-2 border rounded">
                        <select id="purchaseStatus" class="w-full p-2 border rounded">
                            <option value="">Estado de la Compra</option>
                            <option value="ordered">Ordenado</option>
                            <option value="processing">En Proceso</option>
                            <option value="received">Recibido</option>
                        </select>
                        <div id="purchaseItems" class="col-span-3">
                            <!-- Purchase items will be added here dynamically -->
                        </div>
                        <button onclick="addPurchaseItem()" class="bg-green-500 text-white p-2 rounded">Añadir Producto</button>
                        <button onclick="addPurchase()" class="bg-blue-500 text-white p-2 rounded">Crear Orden de Compra</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="min-w-full bg-white">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">ID</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Proveedor</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Fecha</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Estado</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Total</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="purchaseTableBody">
                                <!-- Purchase rows will be added here dynamically -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Warehouse Content -->
                <div id="warehouseContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Diseño del Almacén</h4>
                    <div class="grid grid-cols-5 gap-2" id="warehouseGrid">
                        <!-- Warehouse grid will be generated here -->
                    </div>
                </div>

                <!-- Reports Content -->
                <div id="reportsContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Informes y Análisis</h4>
                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <h5 class="font-semibold mb-2">Ventas por Mes</h5>
                            <canvas id="monthlySalesChart"></canvas>
                        </div>
                        <div>
                            <h5 class="font-semibold mb-2">Inventario por Categoría</h5>
                            <canvas id="inventoryChart"></canvas>
                        </div>
                        <div>
                            <h5 class="font-semibold mb-2">Top 5 Clientes</h5>
                            <canvas id="topCustomersChart"></canvas>
                        </div>
                        <div>
                            <h5 class="font-semibold mb-2">Rendimiento de Proveedores</h5>
                            <canvas id="supplierPerformanceChart"></canvas>
                        </div>
                    </div>
                </div>

                <!-- HR Content -->
                <div id="hrContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Gestión de Recursos Humanos</h4>
                    <div class="mb-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                        <input type="text" id="employeeName" placeholder="Nombre del empleado" class="w-full p-2 border rounded">
                        <input type="email" id="employeeEmail" placeholder="Email del empleado" class="w-full p-2 border rounded">
                        <input type="tel" id="employeePhone" placeholder="Teléfono del empleado" class="w-full p-2 border rounded">
                        <input type="text" id="employeePosition" placeholder="Cargo" class="w-full p-2 border rounded">
                        <input type="text" id="employeeDepartment" placeholder="Departamento" class="w-full p-2 border rounded">
                        <input type="date" id="employeeHireDate" placeholder="Fecha de contratación" class="w-full p-2 border rounded">
                        <button onclick="addEmployee()" class="bg-blue-500 text-white p-2 rounded">Añadir Empleado</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="min-w-full bg-white">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Nombre</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Email</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Cargo</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Departamento</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Fecha de Contratación</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="employeeTableBody">
                                <!-- Employee rows will be added here dynamically -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Finance Content -->
                <div id="financeContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Gestión Financiera</h4>
                    <div class="mb-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                        <input type="date" id="transactionDate" class="w-full p-2 border rounded">
                        <input type="text" id="transactionDescription" placeholder="Descripción" class="w-full p-2 border rounded">
                        <input type="number" id="transactionAmount" placeholder="Monto" class="w-full p-2 border rounded">
                        <select id="transactionType" class="w-full p-2 border rounded">
                            <option value="">Tipo de Transacción</option>
                            <option value="income">Ingreso</option>
                            <option value="expense">Gasto</option>
                        </select>
                        <select id="transactionCategory" class="w-full p-2 border rounded">
                            <option value="">Categoría</option>
                            <option value="sales">Ventas</option>
                            <option value="purchases">Compras</option>
                            <option value="salaries">Salarios</option>
                            <option value="rent">Alquiler</option>
                            <option value="utilities">Servicios</option>
                            <option value="other">Otros</option>
                        </select>
                        <button onclick="addTransaction()" class="bg-blue-500 text-white p-2 rounded">Añadir Transacción</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="min-w-full bg-white">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Fecha</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Descripción</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Tipo</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Categoría</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Monto</th>
                                    <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="transactionTableBody">
                                <!-- Transaction rows will be added here dynamically -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Settings Content -->
                <div id="settingsContent" class="hidden bg-white shadow-md rounded-lg p-6">
                    <h4 class="text-lg font-semibold mb-4">Configuración del Sistema</h4>
                    <div class="space-y-4">
                        <div class="flex items-center justify-between">
                            <label for="notifications" class="font-medium">Notificaciones por email</label>
                            <input type="checkbox" id="notifications" class="form-checkbox h-5 w-5 text-blue-600">
                        </div>
                        <div class="flex items-center justify-between">
                            <label for="darkMode" class="font-medium">Modo oscuro</label>
                            <input type="checkbox" id="darkMode" class="form-checkbox h-5 w-5 text-blue-600">
                        </div>
                        <div>
                            <label for="language" class="font-medium">Idioma</label>
                            <select id="language" class="mt-1 block w-full p-2 border rounded">
                                <option value="es">Español</option>
                                <option value="en">English</option>
                                <option value="fr">Français</option>
                            </select>
                        </div>
                        <div>
                            <label for="currency" class="font-medium">Moneda</label>
                            <select id="currency" class="mt-1 block w-full p-2 border rounded">
                                <option value="eur">Euro (€)</option>
                                <option value="usd">US Dollar ($)</option>
                                <option value="gbp">Pesos ($)</option>
                            </select>
                        </div>
                        <button onclick="saveSettings()" class="bg-blue-500 text-white p-2 rounded">Guardar Configuración</button>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <script>
        // Global variables to store data
        let products = [];
        let customers = [];
        let suppliers = [];
        let orders = [];
        let purchases = [];
        let employees = [];
        let transactions = [];

        // Function to set active tab
        function setActiveTab(tab) {
            // Hide all content divs
            document.querySelectorAll('main > div > div').forEach(div => div.classList.add('hidden'));
            // Show the selected content div
            document.getElementById(tab + 'Content').classList.remove('hidden');
            // Update the section title
            document.getElementById('sectionTitle').textContent = tab.charAt(0).toUpperCase() + tab.slice(1);
            // Update active state in sidebar
            document.querySelectorAll('nav a').forEach(a => a.classList.remove('bg-gray-200'));
            document.querySelector(`nav a[href="#${tab}"]`).classList.add('bg-gray-200');
        }

        // Function to add a product
        function addProduct() {
            const name = document.getElementById('productName').value;
            const quantity = parseInt(document.getElementById('productQuantity').value);
            const price = parseFloat(document.getElementById('productPrice').value);
            const category = document.getElementById('productCategory').value;
            const supplier = document.getElementById('productSupplier').value;
            const location = document.getElementById('productLocation').value;
            const minStock = parseInt(document.getElementById('productMinStock').value);
            const maxStock = parseInt(document.getElementById('productMaxStock').value);
            const sku = document.getElementById('productSKU').value;

            if (name && quantity && price && category && supplier && location && minStock && maxStock && sku) {
                products.push({ id: products.length + 1, name, quantity, price, category, supplier, location, minStock, maxStock, sku });
                updateProductTable();
                // Clear input fields
                document.getElementById('productName').value = '';
                document.getElementById('productQuantity').value = '';
                document.getElementById('productPrice').value = '';
                document.getElementById('productCategory').value = '';
                document.getElementById('productSupplier').value = '';
                document.getElementById('productLocation').value = '';
                document.getElementById('productMinStock').value = '';
                document.getElementById('productMaxStock').value = '';
                document.getElementById('productSKU').value = '';
            } else {
                alert('Por favor, complete todos los campos del producto.');
            }
        }

        // Function to update product table
        function updateProductTable() {
            const tableBody = document.getElementById('productTableBody');
            tableBody.innerHTML = '';
            products.forEach((product, index) => {
                const row = tableBody.insertRow();
                row.innerHTML = `
                    <td class="py-2 px-4 border-b border-gray-200">${product.name}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${product.quantity}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${product.price.toFixed(2)}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${product.category}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${product.supplier}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${product.location}</td>
                    <td class="py-2 px-4 border-b border-gray-200">
                        <button onclick="editProduct(${index})" class="bg-yellow-500 text-white p-1 rounded">Editar</button>
                        <button onclick="deleteProduct(${index})" class="bg-red-500 text-white p-1 rounded ml-2">Eliminar</button>
                    </td>
                `;
            });
        }

        // Function to edit a product
        function editProduct(index) {
            const product = products[index];
            document.getElementById('productName').value = product.name;
            document.getElementById('productQuantity').value = product.quantity;
            document.getElementById('productPrice').value = product.price;
            document.getElementById('productCategory').value = product.category;
            document.getElementById('productSupplier').value = product.supplier;
            document.getElementById('productLocation').value = product.location;
            document.getElementById('productMinStock').value = product.minStock;
            document.getElementById('productMaxStock').value = product.maxStock;
            document.getElementById('productSKU').value = product.sku;
            products.splice(index, 1);
            updateProductTable();
        }

        // Function to delete a product
        function deleteProduct(index) {
            products.splice(index, 1);
            updateProductTable();
        }

        // Function to add a customer
        function addCustomer() {
            const name = document.getElementById('customerName').value;
            const email = document.getElementById('customerEmail').value;
            const phone = document.getElementById('customerPhone').value;
            const address = document.getElementById('customerAddress').value;
            const type = document.getElementById('customerType').value;
            const creditLimit = parseFloat(document.getElementById('customerCreditLimit').value);

            if (name && email && phone && address && type && creditLimit) {
                customers.push({ id: customers.length + 1, name, email, phone, address, type, creditLimit });
                updateCustomerTable();
                // Clear input fields
                document.getElementById('customerName').value = '';
                document.getElementById('customerEmail').value = '';
                document.getElementById('customerPhone').value = '';
                document.getElementById('customerAddress').value = '';
                document.getElementById('customerType').value = '';
                document.getElementById('customerCreditLimit').value = '';
            } else {
                alert('Por favor, complete todos los campos del cliente.');
            }
        }

        // Function to update customer table
        function updateCustomerTable() {
            const tableBody = document.getElementById('customerTableBody');
            tableBody.innerHTML = '';
            customers.forEach((customer, index) => {
                const row = tableBody.insertRow();
                row.innerHTML = `
                    <td class="py-2 px-4 border-b border-gray-200">${customer.name}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${customer.email}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${customer.phone}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${customer.type}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${customer.creditLimit.toFixed(2)}</td>
                    <td class="py-2 px-4 border-b border-gray-200">
                        <button onclick="editCustomer(${index})" class="bg-yellow-500 text-white p-1 rounded">Editar</button>
                        <button onclick="deleteCustomer(${index})" class="bg-red-500 text-white p-1 rounded ml-2">Eliminar</button>
                    </td>
                `;
            });
        }

        // Function to edit a customer
        function editCustomer(index) {
            const customer = customers[index];
            document.getElementById('customerName').value = customer.name;
            document.getElementById('customerEmail').value = customer.email;
            document.getElementById('customerPhone').value = customer.phone;
            document.getElementById('customerAddress').value = customer.address;
            document.getElementById('customerType').value = customer.type;
            document.getElementById('customerCreditLimit').value = customer.creditLimit;
            customers.splice(index, 1);
            updateCustomerTable();
        }

        // Function to delete a customer
        function deleteCustomer(index) {
            customers.splice(index, 1);
            updateCustomerTable();
        }

        // Function to add a supplier
        function addSupplier() {
            const name = document.getElementById('supplierName').value;
            const email = document.getElementById('supplierEmail').value;
            const phone = document.getElementById('supplierPhone').value;
            const address = document.getElementById('supplierAddress').value;
            const product = document.getElementById('supplierProduct').value;
            const leadTime = parseInt(document.getElementById('supplierLeadTime').value);

            if (name && email && phone && address && product && leadTime) {
                suppliers.push({ id: suppliers.length + 1, name, email, phone, address, product, leadTime });
                updateSupplierTable();
                // Clear input fields
                document.getElementById('supplierName').value = '';
                document.getElementById('supplierEmail').value = '';
                document.getElementById('supplierPhone').value = '';
                document.getElementById('supplierAddress').value = '';
                document.getElementById('supplierProduct').value = '';
                document.getElementById('supplierLeadTime').value = '';
            } else {
                alert('Por favor, complete todos los campos del proveedor.');
            }
        }

        // Function to update supplier table
        function updateSupplierTable() {
            const tableBody = document.getElementById('supplierTableBody');
            tableBody.innerHTML = '';
            suppliers.forEach((supplier, index) => {
                const row = tableBody.insertRow();
                row.innerHTML = `
                    <td class="py-2 px-4 border-b border-gray-200">${supplier.name}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${supplier.email}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${supplier.phone}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${supplier.product}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${supplier.leadTime} días</td>
                    <td class="py-2 px-4 border-b border-gray-200">
                        <button onclick="editSupplier(${index})" class="bg-yellow-500 text-white p-1 rounded">Editar</button>
                        <button onclick="deleteSupplier(${index})" class="bg-red-500 text-white p-1 rounded ml-2">Eliminar</button>
                    </td>
                `;
            });
        }

        // Function to edit a supplier
        function editSupplier(index) {
            const supplier = suppliers[index];
            document.getElementById('supplierName').value = supplier.name;
            document.getElementById('supplierEmail').value = supplier.email;
            document.getElementById('supplierPhone').value = supplier.phone;
            document.getElementById('supplierAddress').value = supplier.address;
            document.getElementById('supplierProduct').value = supplier.product;
            document.getElementById('supplierLeadTime').value = supplier.leadTime;
            suppliers.splice(index, 1);
            updateSupplierTable();
        }

        // Function to delete a supplier
        function deleteSupplier(index) {
            suppliers.splice(index, 1);
            updateSupplierTable();
        }

        // Function to add an order item
        function addOrderItem() {
            const orderItems = document.getElementById('orderItems');
            const itemIndex = orderItems.children.length;
            const itemDiv = document.createElement('div');
            itemDiv.className = 'grid grid-cols-3 gap-2 mb-2';
            itemDiv.innerHTML = `
                <select id="orderItem${itemIndex}" class="w-full p-2 border rounded">
                    <option value="">Seleccionar Producto</option>
                    ${products.map(product => `<option value="${product.id}">${product.name}</option>`).join('')}
                </select>
                <input type="number" id="orderItemQuantity${itemIndex}" placeholder="Cantidad" class="w-full p-2 border rounded">
                <button onclick="removeOrderItem(${itemIndex})" class="bg-red-500 text-white p-2 rounded">Eliminar</button>
            `;
            orderItems.appendChild(itemDiv);
        }

        // Function to remove an order item
        function removeOrderItem(index) {
            const orderItems = document.getElementById('orderItems');
            orderItems.removeChild(orderItems.children[index]);
        }

        // Function to add an order
        function addOrder() {
            const customer = document.getElementById('orderCustomer').value;
            const date = document.getElementById('orderDate').value;
            const status = document.getElementById('orderStatus').value;
            const items = [];
            const orderItems = document.getElementById('orderItems').children;
            let total = 0;

            for (let i = 0; i < orderItems.length; i++) {
                const productId = document.getElementById(`orderItem${i}`).value;
                const quantity = parseInt(document.getElementById(`orderItemQuantity${i}`).value);
                const product = products.find(p => p.id === parseInt(productId));
                if (product && quantity) {
                    items.push({ product: product.name, quantity, price: product.price });
                    total += product.price * quantity;
                }
            }

            if (customer && date && status && items.length > 0) {
                orders.push({ id: orders.length + 1, customer, date, status, items, total });
                updateOrderTable();
                // Clear input fields
                document.getElementById('orderCustomer').value = '';
                document.getElementById('orderDate').value = '';
                document.getElementById('orderStatus').value = '';
                document.getElementById('orderItems').innerHTML = '';
            } else {
                alert('Por favor, complete todos los campos del pedido y añada al menos un producto.');
            }
        }

        // Function to update order table
        function updateOrderTable() {
            const tableBody = document.getElementById('orderTableBody');
            tableBody.innerHTML = '';
            orders.forEach((order, index) => {
                const row = tableBody.insertRow();
                row.innerHTML = `
                    <td class="py-2 px-4 border-b border-gray-200">${order.id}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${order.customer}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${order.date}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${order.status}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${order.total.toFixed(2)}</td>
                    <td class="py-2 px-4 border-b border-gray-200">
                        <button onclick="viewOrder(${index})" class="bg-blue-500 text-white p-1 rounded">Ver</button>
                        <button onclick="editOrder(${index})" class="bg-yellow-500 text-white p-1 rounded ml-2">Editar</button>
                        <button onclick="deleteOrder(${index})" class="bg-red-500 text-white p-1 rounded ml-2">Eliminar</button>
                    </td>
                `;
            });
        }

        // Function to view an order
        function viewOrder(index) {
            const order = orders[index];
            let itemsHtml = order.items.map(item => `
                <tr>
                    <td class="py-2 px-4 border-b border-gray-200">${item.product}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${item.quantity}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${item.price.toFixed(2)}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${(item.quantity * item.price).toFixed(2)}</td>
                </tr>
            `).join('');

            const orderDetails = `
                <h2 class="text-xl font-bold mb-4">Detalles del Pedido #${order.id}</h2>
                <p><strong>Cliente:</strong> ${order.customer}</p>
                <p><strong>Fecha:</strong> ${order.date}</p>
                <p><strong>Estado:</strong> ${order.status}</p>
                <h3 class="text-lg font-semibold mt-4 mb-2">Productos:</h3>
                <table class="min-w-full bg-white">
                    <thead>
                        <tr>
                            <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Producto</th>
                            <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Cantidad</th>
                            <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Precio Unitario</th>
                            <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Subtotal</th>
                        </tr>
                    </thead>
                    <tbody>
                        ${itemsHtml}
                    </tbody>
                </table>
                <p class="mt-4"><strong>Total:</strong> $${order.total.toFixed(2)}</p>
            `;

            // Create a modal to display the order details
            const modal = document.createElement('div');
            modal.className = 'fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full';
            modal.innerHTML = `
                <div class="relative top-20 mx-auto p-5 border w-96 shadow-lg rounded-md bg-white">
                    <div class="mt-3 text-center">
                        ${orderDetails}
                        <div class="items-center px-4 py-3">
                            <button id="closeModal" class="px-4 py-2 bg-blue-500 text-white text-base font-medium rounded-md w-full shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-300">
                                Cerrar
                            </button>
                        </div>
                    </div>
                </div>
            `;
            document.body.appendChild(modal);

            // Close the modal when the close button is clicked
            document.getElementById('closeModal').onclick = function() {
                document.body.removeChild(modal);
            }
        }

        // Function to edit an order
        function editOrder(index) {
            const order = orders[index];
            document.getElementById('orderCustomer').value = order.customer;
            document.getElementById('orderDate').value = order.date;
            document.getElementById('orderStatus').value = order.status;
            document.getElementById('orderItems').innerHTML = '';
            order.items.forEach((item, i) => {
                addOrderItem();
                document.getElementById(`orderItem${i}`).value = products.find(p => p.name === item.product).id;
                document.getElementById(`orderItemQuantity${i}`).value = item.quantity;
            });
            orders.splice(index, 1);
            updateOrderTable();
        }

        // Function to delete an order
        function deleteOrder(index) {
            orders.splice(index, 1);
            updateOrderTable();
        }

        // Function to add a purchase item
        function addPurchaseItem() {
            const purchaseItems = document.getElementById('purchaseItems');
            const itemIndex = purchaseItems.children.length;
            const itemDiv = document.createElement('div');
            itemDiv.className = 'grid grid-cols-3 gap-2 mb-2';
            itemDiv.innerHTML = `
                <select id="purchaseItem${itemIndex}" class="w-full p-2 border rounded">
                    <option value="">Seleccionar Producto</option>
                    ${products.map(product => `<option value="${product.id}">${product.name}</option>`).join('')}
                </select>
                <input type="number" id="purchaseItemQuantity${itemIndex}" placeholder="Cantidad" class="w-full p-2 border rounded">
                <button onclick="removePurchaseItem(${itemIndex})" class="bg-red-500 text-white p-2 rounded">Eliminar</button>
            `;
            purchaseItems.appendChild(itemDiv);
        }

        // Function to remove a purchase item
        function removePurchaseItem(index) {
            const purchaseItems = document.getElementById('purchaseItems');
            purchaseItems.removeChild(purchaseItems.children[index]);
        }

        // Function to add a purchase
        function addPurchase() {
            const supplier = document.getElementById('purchaseSupplier').value;
            const date = document.getElementById('purchaseDate').value;
            const status = document.getElementById('purchaseStatus').value;
            const items = [];
            const purchaseItems = document.getElementById('purchaseItems').children;
            let total = 0;

            for (let i = 0; i < purchaseItems.length; i++) {
                const productId = document.getElementById(`purchaseItem${i}`).value;
                const quantity = parseInt(document.getElementById(`purchaseItemQuantity${i}`).value);
                const product = products.find(p => p.id === parseInt(productId));
                if (product && quantity) {
                    items.push({ product: product.name, quantity, price: product.price });
                    total += product.price * quantity;
                }
            }

            if (supplier && date && status && items.length > 0) {
                purchases.push({ id: purchases.length + 1, supplier, date, status, items, total });
                updatePurchaseTable();
                // Clear input fields
                document.getElementById('purchaseSupplier').value = '';
                document.getElementById('purchaseDate').value = '';
                document.getElementById('purchaseStatus').value = '';
                document.getElementById('purchaseItems').innerHTML = '';
            } else {
                alert('Por favor, complete todos los campos de la compra y añada al menos un producto.');
            }
        }

        // Function to update purchase table
        function updatePurchaseTable() {
            const tableBody = document.getElementById('purchaseTableBody');
            tableBody.innerHTML = '';
            purchases.forEach((purchase, index) => {
                const row = tableBody.insertRow();
                row.innerHTML = `
                    <td class="py-2 px-4 border-b border-gray-200">${purchase.id}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${purchase.supplier}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${purchase.date}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${purchase.status}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${purchase.total.toFixed(2)}</td>
                    <td class="py-2 px-4 border-b border-gray-200">
                        <button onclick="viewPurchase(${index})" class="bg-blue-500 text-white p-1 rounded">Ver</button>
                        <button onclick="editPurchase(${index})" class="bg-yellow-500 text-white p-1 rounded ml-2">Editar</button>
                        <button onclick="deletePurchase(${index})" class="bg-red-500 text-white p-1 rounded ml-2">Eliminar</button>
                    </td>
                `;
            });
        }

        // Function to view a purchase
        function viewPurchase(index) {
            const purchase = purchases[index];
            let itemsHtml = purchase.items.map(item => `
                <tr>
                    <td class="py-2 px-4 border-b border-gray-200">${item.product}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${item.quantity}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${item.price.toFixed(2)}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${(item.quantity * item.price).toFixed(2)}</td>
                </tr>
            `).join('');

            const purchaseDetails = `
                <h2 class="text-xl font-bold mb-4">Detalles de la Compra #${purchase.id}</h2>
                <p><strong>Proveedor:</strong> ${purchase.supplier}</p>
                <p><strong>Fecha:</strong> ${purchase.date}</p>
                <p><strong>Estado:</strong> ${purchase.status}</p>
                <h3 class="text-lg font-semibold mt-4 mb-2">Productos:</h3>
                <table class="min-w-full bg-white">
                    <thead>
                        <tr>
                            <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Producto</th>
                            <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Cantidad</th>
                            <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Precio Unitario</th>
                            <th class="py-2 px-4 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">Subtotal</th>
                        </tr>
                    </thead>
                    <tbody>
                        ${itemsHtml}
                    </tbody>
                </table>
                <p class="mt-4"><strong>Total:</strong> $${purchase.total.toFixed(2)}</p>
            `;

            // Create a modal to display the purchase details
            const modal = document.createElement('div');
            modal.className = 'fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full';
            modal.innerHTML = `
                <div class="relative top-20 mx-auto p-5 border w-96 shadow-lg rounded-md bg-white">
                    <div class="mt-3 text-center">
                        ${purchaseDetails}
                        <div class="items-center px-4 py-3">
                            <button id="closeModal" class="px-4 py-2 bg-blue-500 text-white text-base font-medium rounded-md w-full shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-300">
                                Cerrar
                            </button>
                        </div>
                    </div>
                </div>
            `;
            document.body.appendChild(modal);

            // Close the modal when the close button is clicked
            document.getElementById('closeModal').onclick = function() {
                document.body.removeChild(modal);
            }
        }

        // Function to edit a purchase
        function editPurchase(index) {
            const purchase = purchases[index];
            document.getElementById('purchaseSupplier').value = purchase.supplier;
            document.getElementById('purchaseDate').value = purchase.date;
            document.getElementById('purchaseStatus').value = purchase.status;
            document.getElementById('purchaseItems').innerHTML = '';
            purchase.items.forEach((item, i) => {
                addPurchaseItem();
                document.getElementById(`purchaseItem${i}`).value = products.find(p => p.name === item.product).id;
                document.getElementById(`purchaseItemQuantity${i}`).value = item.quantity;
            });
            purchases.splice(index, 1);
            updatePurchaseTable();
        }

        // Function to delete a purchase
        function deletePurchase(index) {
            purchases.splice(index, 1);
            updatePurchaseTable();
        }

        // Function to generate warehouse grid
        function generateWarehouseGrid() {
            const grid = document.getElementById('warehouseGrid');
            for (let i = 0; i < 25; i++) {
                const cell = document.createElement('div');
                cell.className = 'bg-gray-200 p-4 text-center';
                cell.textContent = String.fromCharCode(65 + Math.floor(i / 5)) + (i % 5 + 1);
                cell.onclick = function() {
                    const product = products.find(p => p.location === this.textContent);
                    if (product) {
                        alert(`Ubicación: ${this.textContent}\nProducto: ${product.name}\nCantidad: ${product.quantity}`);
                    } else {
                        alert(`Ubicación: ${this.textContent}\nVacía`);
                    }
                };
                grid.appendChild(cell);
            }
        }

        // Function to save settings
        function saveSettings() {
            const notifications = document.getElementById('notifications').checked;
            const darkMode = document.getElementById('darkMode').checked;
            const language = document.getElementById('language').value;
            const currency = document.getElementById('currency').value;
            // Here you would typically save these settings to a backend or local storage
            console.log('Settings saved:', { notifications, darkMode, language, currency });
            alert('Configuración guardada');
        }

        // Function to add an employee
        function addEmployee() {
            const name = document.getElementById('employeeName').value;
            const email = document.getElementById('employeeEmail').value;
            const phone = document.getElementById('employeePhone').value;
            const position = document.getElementById('employeePosition').value;
            const department = document.getElementById('employeeDepartment').value;
            const hireDate = document.getElementById('employeeHireDate').value;

            if (name && email && phone && position && department && hireDate) {
                employees.push({ id: employees.length + 1, name, email, phone, position, department, hireDate });
                updateEmployeeTable();
                // Clear input fields
                document.getElementById('employeeName').value = '';
                document.getElementById('employeeEmail').value = '';
                document.getElementById('employeePhone').value = '';
                document.getElementById('employeePosition').value = '';
                document.getElementById('employeeDepartment').value = '';
                document.getElementById('employeeHireDate').value = '';
            } else {
                alert('Por favor, complete todos los campos del empleado.');
            }
        }

        // Function to update employee table
        function updateEmployeeTable() {
            const tableBody = document.getElementById('employeeTableBody');
            tableBody.innerHTML = '';
            employees.forEach((employee, index) => {
                const row = tableBody.insertRow();
                row.innerHTML = `
                    <td class="py-2 px-4 border-b border-gray-200">${employee.name}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${employee.email}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${employee.position}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${employee.department}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${employee.hireDate}</td>
                    <td class="py-2 px-4 border-b border-gray-200">
                        <button onclick="editEmployee(${index})" class="bg-yellow-500 text-white p-1 rounded">Editar</button>
                        <button onclick="deleteEmployee(${index})" class="bg-red-500 text-white p-1 rounded ml-2">Eliminar</button>
                    </td>
                `;
            });
        }

        // Function to edit an employee
        function editEmployee(index) {
            const employee = employees[index];
            document.getElementById('employeeName').value = employee.name;
            document.getElementById('employeeEmail').value = employee.email;
            document.getElementById('employeePhone').value = employee.phone;
            document.getElementById('employeePosition').value = employee.position;
            document.getElementById('employeeDepartment').value = employee.department;
            document.getElementById('employeeHireDate').value = employee.hireDate;
            employees.splice(index, 1);
            updateEmployeeTable();
        }

        // Function to delete an employee
        function deleteEmployee(index) {
            employees.splice(index, 1);
            updateEmployeeTable();
        }

        // Function to add a transaction
        function addTransaction() {
            const date = document.getElementById('transactionDate').value;
            const description = document.getElementById('transactionDescription').value;
            const amount = parseFloat(document.getElementById('transactionAmount').value);
            const type = document.getElementById('transactionType').value;
            const category = document.getElementById('transactionCategory').value;

            if (date && description && amount && type && category) {
                transactions.push({ id: transactions.length + 1, date, description, amount, type, category });
                updateTransactionTable();
                // Clear input fields
                document.getElementById('transactionDate').value = '';
                document.getElementById('transactionDescription').value = '';
                document.getElementById('transactionAmount').value = '';
                document.getElementById('transactionType').value = '';
                document.getElementById('transactionCategory').value = '';
            } else {
                alert('Por favor, complete todos los campos de la transacción.');
            }
        }

        // Function to update transaction table
        function updateTransactionTable() {
            const tableBody = document.getElementById('transactionTableBody');
            tableBody.innerHTML = '';
            transactions.forEach((transaction, index) => {
                const row = tableBody.insertRow();
                row.innerHTML = `
                    <td class="py-2 px-4 border-b border-gray-200">${transaction.date}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${transaction.description}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${transaction.type}</td>
                    <td class="py-2 px-4 border-b border-gray-200">${transaction.category}</td>
                    <td class="py-2 px-4 border-b border-gray-200">$${transaction.amount.toFixed(2)}</td>
                    <td class="py-2 px-4 border-b border-gray-200">
                        <button onclick="editTransaction(${index})" class="bg-yellow-500 text-white p-1 rounded">Editar</button>
                        <button onclick="deleteTransaction(${index})" class="bg-red-500 text-white p-1 rounded ml-2">Eliminar</button>
                    </td>
                `;
            });
        }

        // Function to edit a transaction
        function editTransaction(index) {
            const transaction = transactions[index];
            document.getElementById('transactionDate').value = transaction.date;
            document.getElementById('transactionDescription').value = transaction.description;
            document.getElementById('transactionAmount').value = transaction.amount;
            document.getElementById('transactionType').value = transaction.type;
            document.getElementById('transactionCategory').value = transaction.category;
            transactions.splice(index, 1);
            updateTransactionTable();
        }

        // Function to delete a transaction
        function deleteTransaction(index) {
            transactions.splice(index, 1);
            updateTransactionTable();
        }

        // Function to show notifications
        function showNotifications() {
            alert('Función de notificaciones en desarrollo');
        }

        // Function to show help
        function showHelp() {
            alert('Función de ayuda en desarrollo');
        }

        // Initialize charts
        function initializeCharts() {
            // Sales Chart
            const salesCtx = document.getElementById('salesChart').getContext('2d');
            new Chart(salesCtx, {
                type: 'line',
                data: {
                    labels: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun'],
                    datasets: [{
                        label: 'Ventas',
                        data: [12, 19, 3, 5, 2, 3],
                        borderColor: 'rgb(75, 192, 192)',
                        tension: 0.1
                    }]
                }
            });

            // Top Products Chart
            const topProductsCtx = document.getElementById('topProductsChart').getContext('2d');
            new Chart(topProductsCtx, {
                type: 'pie',
                data: {
                    labels: ['Producto A', 'Producto B', 'Producto C', 'Producto D'],
                    datasets: [{
                        data: [12, 19, 3, 5],
                        backgroundColor: [
                            'rgba(255, 99, 132, 0.8)',
                            'rgba(54, 162, 235, 0.8)',
                            'rgba(255, 206, 86, 0.8)',
                            'rgba(75, 192, 192, 0.8)'
                        ]
                    }]
                }
            });

            // Monthly Sales Chart
            const monthlySalesCtx = document.getElementById('monthlySalesChart').getContext('2d');
            new Chart(monthlySalesCtx, {
                type: 'bar',
                data: {
                    labels: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun'],
                    datasets: [{
                        label: 'Ventas Mensuales',
                        data: [65, 59, 80, 81, 56, 55],
                        backgroundColor: 'rgba(54, 162, 235, 0.8)'
                    }]
                }
            });

            // Inventory Chart
            const inventoryCtx = document.getElementById('inventoryChart').getContext('2d');
            new Chart(inventoryCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Electrónica', 'Ropa', 'Alimentos', 'Muebles'],
                    datasets: [{
                        data: [300, 50, 100, 80],
                        backgroundColor: [
                            'rgba(255, 99, 132, 0.8)',
                            'rgba(54, 162, 235, 0.8)',
                            'rgba(255, 206, 86, 0.8)',
                            'rgba(75, 192, 192, 0.8)'
                        ]
                    }]
                }
            });

            // Top Customers Chart
            const topCustomersCtx = document.getElementById('topCustomersChart').getContext('2d');
            new Chart(topCustomersCtx, {
                type: 'horizontalBar',
                data: {
                    labels: ['Cliente A', 'Cliente B', 'Cliente C', 'Cliente D', 'Cliente E'],
                    datasets: [{
                        label: 'Ventas Totales',
                        data: [12000, 9000, 7500, 6000, 4500],
                        backgroundColor: 'rgba(153, 102, 255, 0.8)'
                    }]
                },
                options: {
                    scales: {
                        xAxes: [{
                            ticks: {
                                beginAtZero: true
                            }
                        }]
                    }
                }
            });

            // Supplier Performance Chart
            const supplierPerformanceCtx = document.getElementById('supplierPerformanceChart').getContext('2d');
            new Chart(supplierPerformanceCtx, {
                type: 'radar',
                data: {
                    labels: ['Calidad', 'Puntualidad', 'Precio', 'Comunicación', 'Flexibilidad'],
                    datasets: [{
                        label: 'Proveedor A',
                        data: [85, 90, 75, 80, 70],
                        backgroundColor: 'rgba(255, 99, 132, 0.2)',
                        borderColor: 'rgb(255, 99, 132)',
                        pointBackgroundColor: 'rgb(255, 99, 132)'
                    }, {
                        label: 'Proveedor B',
                        data: [70, 85, 90, 75, 80],
                        backgroundColor: 'rgba(54, 162, 235, 0.2)',
                        borderColor: 'rgb(54, 162, 235)',
                        pointBackgroundColor: 'rgb(54, 162, 235)'
                    }]
                },
                options: {
                    scale: {
                        ticks: {
                            beginAtZero: true,
                            max: 100
                        }
                    }
                }
            });

            // Employee Performance Chart
            const employeePerformanceCtx = document.getElementById('employeePerformanceChart').getContext('2d');
            new Chart(employeePerformanceCtx, {
                type: 'bar',
                data: {
                    labels: ['Empleado A', 'Empleado B', 'Empleado C', 'Empleado D', 'Empleado E'],
                    datasets: [{
                        label: 'Rendimiento',
                        data: [85, 90, 75, 80, 95],
                        backgroundColor: 'rgba(75, 192, 192, 0.8)'
                    }]
                },
                options: {
                    scales: {
                        yAxes: [{
                            ticks: {
                                beginAtZero: true,
                                max: 100
                            }
                        }]
                    }
                }
            });
        }

        // Function to update KPIs
        function updateKPIs() {
            // These values would typically come from calculations based on your data
            document.getElementById('monthlySalesKPI').textContent = '75%';
            document.getElementById('customerSatisfactionKPI').textContent = '90%';
            document.getElementById('warehouseEfficiencyKPI').textContent = '60%';
        }

        // Function to update recent alerts
        function updateRecentAlerts() {
            const alertsList = document.getElementById('recentAlerts');
            const alerts = [
                { message: 'Stock bajo para Producto A', type: 'warning' },
                { message: 'Nuevo pedido recibido', type: 'info' },
                { message: 'Pago vencido del Cliente X', type: 'danger' }
            ];

            alertsList.innerHTML = alerts.map(alert => `
                <li class="flex items-center ${alert.type === 'warning' ? 'text-yellow-600' : alert.type === 'danger' ? 'text-red-600' : 'text-blue-600'}">
                    <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                    </svg>
                    ${alert.message}
                </li>
            `).join('');
        }

        // Function to update pending tasks
        function updatePendingTasks() {
            const tasksList = document.getElementById('pendingTasks');
            const tasks = [
                { task: 'Revisar inventario', dueDate: '2023-07-20' },
                { task: 'Contactar nuevos clientes', dueDate: '2023-07-22' },
                { task: 'Preparar informe mensual', dueDate: '2023-07-31' }
            ];

            tasksList.innerHTML = tasks.map(task => `
                <li class="flex items-center justify-between">
                    <span>${task.task}</span>
                    <span class="text-sm text-gray-500">${task.dueDate}</span>
                </li>
            `).join('');
        }

        // Initialize the application
        function init() {
            setActiveTab('dashboard');
            generateWarehouseGrid();
            initializeCharts();
            updateKPIs();
            updateRecentAlerts();
            updatePendingTasks();
        }

        // Call init when the page loads
        window.onload = init;
    </script>
</body>
</html>
