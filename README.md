"use client"

import { useState, useEffect } from "react"
import { Button } from "@/components/ui/button"
import { Input } from "@/components/ui/input"
import { Table, TableBody, TableCell, TableHead, TableHeader, TableRow } from "@/components/ui/table"
import { Dialog, DialogContent, DialogHeader, DialogTitle, DialogTrigger } from "@/components/ui/dialog"
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from "@/components/ui/select"
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs"
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "@/components/ui/card"
import { Label } from "@/components/ui/label"
import { Textarea } from "@/components/ui/textarea"
import { Calendar } from "@/components/ui/calendar"
import { BarChart, Bar, LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer, PieChart, Pie, Cell, AreaChart, Area } from 'recharts'
import { Badge } from "@/components/ui/badge"
import { Switch } from "@/components/ui/switch"
import { Slider } from "@/components/ui/slider"
import { Progress } from "@/components/ui/progress"
import { Checkbox } from "@/components/ui/checkbox"
import { ScrollArea } from "@/components/ui/scroll-area"
import { Avatar, AvatarFallback, AvatarImage } from "@/components/ui/avatar"
import { Popover, PopoverContent, PopoverTrigger } from "@/components/ui/popover"
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from "@/components/ui/accordion"
import { AlertDialog, AlertDialogAction, AlertDialogCancel, AlertDialogContent, AlertDialogDescription, AlertDialogFooter, AlertDialogHeader, AlertDialogTitle, AlertDialogTrigger } from "@/components/ui/alert-dialog"
import { CalendarIcon, ChevronDownIcon, ChevronUpIcon, Package, ShoppingCart, Users, Truck, DollarSign, BarChart2, Settings, HelpCircle, Bell, Search, Menu, FileText, Clipboard, Map, Activity, Zap, Shield, Gift, Coffee, Briefcase } from "lucide-react"

export default function Component() {
  const [activeTab, setActiveTab] = useState("dashboard")
  const [products, setProducts] = useState([
    { id: 1, name: "Producto A", quantity: 100, price: 10, maxStock: 150, minStock: 50, level: "A", location: "A1", supplier: "Proveedor X", category: "Electrónica", sku: "SKU001", barcode: "123456789", weight: 0.5, dimensions: "10x5x2", reorderPoint: 75, lastRestocked: "2023-05-15", expirationDate: "2024-12-31", cost: 8, profit: 2, salesVelocity: 10 },
    { id: 2, name: "Producto B", quantity: 75, price: 15, maxStock: 100, minStock: 25, level: "B", location: "B2", supplier: "Proveedor Y", category: "Ropa", sku: "SKU002", barcode: "987654321", weight: 0.3, dimensions: "20x15x5", reorderPoint: 50, lastRestocked: "2023-06-01", expirationDate: "2025-06-30", cost: 12, profit: 3, salesVelocity: 5 },
  ])
  const [customers, setCustomers] = useState([
    { id: 1, name: "Cliente 1", email: "cliente1@example.com", phone: "123-456-7890", address: "Calle 123, Ciudad", paymentMethod: "Tarjeta", creditLimit: 1000, balance: 500, lastPurchase: "2023-07-01", loyaltyPoints: 100, customerSegment: "VIP" },
    { id: 2, name: "Cliente 2", email: "cliente2@example.com", phone: "098-765-4321", address: "Avenida 456, Pueblo", paymentMethod: "Efectivo", creditLimit: 500, balance: 0, lastPurchase: "2023-06-15", loyaltyPoints: 50, customerSegment: "Regular" },
  ])
  const [suppliers, setSuppliers] = useState([
    { id: 1, name: "Proveedor X", email: "proveedorx@example.com", phone: "111-222-3333", address: "Polígono Industrial 1, Ciudad", paymentTerms: "30 días", rating: 4.5, lastOrder: "2023-06-20", leadTime: 5, minimumOrderQuantity: 100, preferredShippingMethod: "Terrestre" },
    { id: 2, name: "Proveedor Y", email: "proveedory@example.com", phone: "444-555-6666", address: "Zona Comercial 2, Pueblo", paymentTerms: "15 días", rating: 4.0, lastOrder: "2023-07-05", leadTime: 3, minimumOrderQuantity: 50, preferredShippingMethod: "Aéreo" },
  ])
  const [orders, setOrders] = useState([
    { id: 1, customer: "Cliente 1", date: "2023-07-10", status: "Enviado", total: 150, items: [{ product: "Producto A", quantity: 10, price: 10 }, { product: "Producto B", quantity: 5, price: 15 }], shippingMethod: "Express", trackingNumber: "TR123456", estimatedDelivery: "2023-07-15" },
    { id: 2, customer: "Cliente 2", date: "2023-07-12", status: "Pendiente", total: 75, items: [{ product: "Producto B", quantity: 5, price: 15 }], shippingMethod: "Estándar", trackingNumber: "", estimatedDelivery: "2023-07-20" },
  ])
  const [purchaseOrders, setPurchaseOrders] = useState([
    { id: 1, supplier: "Proveedor X", date: "2023-07-05", status: "Recibido", total: 1000, items: [{ product: "Producto A", quantity: 100, price: 10 }], paymentStatus: "Pagado", invoiceNumber: "INV001" },
    { id: 2, supplier: "Proveedor Y", date: "2023-07-08", status: "En tránsito", total: 750, items: [{ product: "Producto B", quantity: 50, price: 15 }], paymentStatus: "Pendiente", invoiceNumber: "INV002" },
  ])
  const [employees, setEmployees] = useState([
    { id: 1, name: "Empleado 1", position: "Gerente de Ventas", department: "Ventas", email: "empleado1@example.com", phone: "111-111-1111", hireDate: "2020-01-15", salary: 50000, performance: 4.5 },
    { id: 2, name: "Empleado 2", position: "Asistente de Almacén", department: "Logística", email: "empleado2@example.com", phone: "222-222-2222", hireDate: "2021-03-01", salary: 30000, performance: 4.0 },
  ])
  const [tasks, setTasks] = useState([
    { id: 1, title: "Revisar inventario", assignedTo: "Empleado 2", dueDate: "2023-07-20", status: "En progreso", priority: "Alta" },
    { id: 2, title: "Contactar nuevos clientes", assignedTo: "Empleado 1", dueDate: "2023-07-25", status: "Pendiente", priority: "Media" },
  ])
  const [expenses, setExpenses] = useState([
    { id: 1, category: "Suministros de oficina", amount: 500, date: "2023-07-01", approvedBy: "Empleado 1", paymentMethod: "Tarjeta corporativa" },
    { id: 2, category: "Mantenimiento de equipos", amount: 1000, date: "2023-07-05", approvedBy: "Empleado 1", paymentMethod: "Transferencia bancaria" },
  ])

  const [newProduct, setNewProduct] = useState({
    name: "", quantity: 0, price: 0, maxStock: 0, minStock: 0, level: "", location: "", supplier: "", category: "", sku: "", barcode: "", weight: 0, dimensions: "", reorderPoint: 0, lastRestocked: "", expirationDate: "", cost: 0, profit: 0, salesVelocity: 0
  })
  const [newCustomer, setNewCustomer] = useState({ name: "", email: "", phone: "", address: "", paymentMethod: "", creditLimit: 0, balance: 0, lastPurchase: "", loyaltyPoints: 0, customerSegment: "" })
  const [newSupplier, setNewSupplier] = useState({ name: "", email: "", phone: "", address: "", paymentTerms: "", rating: 0, lastOrder: "", leadTime: 0, minimumOrderQuantity: 0, preferredShippingMethod: "" })
  const [newOrder, setNewOrder] = useState({ customer: "", date: "", status: "", total: 0, items: [], shippingMethod: "", trackingNumber: "", estimatedDelivery: "" })
  const [newPurchaseOrder, setNewPurchaseOrder] = useState({ supplier: "", date: "", status: "", total: 0, items: [], paymentStatus: "", invoiceNumber: "" })
  const [newEmployee, setNewEmployee] = useState({ name: "", position: "", department: "", email: "", phone: "", hireDate: "", salary: 0, performance: 0 })
  const [newTask, setNewTask] = useState({ title: "", assignedTo: "", dueDate: "", status: "", priority: "" })
  const [newExpense, setNewExpense] = useState({ category: "", amount: 0, date: "", approvedBy: "", paymentMethod: "" })

  const [editingProduct, setEditingProduct] = useState(null)
  const [editingCustomer, setEditingCustomer] = useState(null)
  const [editingSupplier, setEditingSupplier] = useState(null)
  const [editingOrder, setEditingOrder] = useState(null)
  const [editingPurchaseOrder, setEditingPurchaseOrder] = useState(null)
  const [editingEmployee, setEditingEmployee] = useState(null)
  const [editingTask, setEditingTask] = useState(null)
  const [editingExpense, setEditingExpense] = useState(null)

  const handleAddProduct = () => {
    setProducts([...products, { ...newProduct, id: products.length + 1 }])
    setNewProduct({ name: "", quantity: 0, price: 0, maxStock: 0, minStock: 0, level: "", location: "", supplier: "", category: "", sku: "", barcode: "", weight: 0, dimensions: "", reorderPoint: 0, lastRestocked: "", expirationDate: "", cost: 0, profit: 0, salesVelocity: 0 })
  }

  const handleEditProduct = (product) => {
    setEditingProduct(product)
  }

  const handleUpdateProduct = () => {
    setProducts(products.map(p => p.id === editingProduct.id ? editingProduct : p))
    setEditingProduct(null)
  }

  const handleDeleteProduct = (id) => {
    setProducts(products.filter(p => p.id !== id))
  }

  const handleAddCustomer = () => {
    setCustomers([...customers, { ...newCustomer, id: customers.length + 1 }])
    setNewCustomer({ name: "", email: "", phone: "", address: "", paymentMethod: "", creditLimit: 0, balance: 0, lastPurchase: "", loyaltyPoints: 0, customerSegment: "" })
  }

  const handleEditCustomer = (customer) => {
    setEditingCustomer(customer)
  }

  const handleUpdateCustomer = () => {
    setCustomers(customers.map(c => c.id === editingCustomer.id ? editingCustomer : c))
    setEditingCustomer(null)
  }

  const handleDeleteCustomer = (id) => {
    setCustomers(customers.filter(c => c.id !== id))
  }

  const handleAddSupplier = () => {
    setSuppliers([...suppliers, { ...newSupplier, id: suppliers.length + 1 }])
    setNewSupplier({ name: "", email: "", phone: "", address: "", paymentTerms: "", rating: 0, lastOrder: "", leadTime: 0, minimumOrderQuantity: 0, preferredShippingMethod: "" })
  }

  const handleEditSupplier = (supplier) => {
    setEditingSupplier(supplier)
  }

  const handleUpdateSupplier = () => {
    setSuppliers(suppliers.map(s => s.id === editingSupplier.id ? editingSupplier : s))
    setEditingSupplier(null)
  }

  const handleDeleteSupplier = (id) => {
    setSuppliers(suppliers.filter(s => s.id !== id))
  }

  const handleAddOrder = () => {
    setOrders([...orders, { ...newOrder, id: orders.length + 1 }])
    setNewOrder({ customer: "", date: "", status: "", total: 0, items: [], shippingMethod: "", trackingNumber: "", estimatedDelivery: "" })
  }

  const handleEditOrder = (order) => {
    setEditingOrder(order)
  }

  const handleUpdateOrder = () => {
    setOrders(orders.map(o => o.id === editingOrder.id ? editingOrder : o))
    setEditingOrder(null)
  }

  const handleDeleteOrder = (id) => {
    setOrders(orders.filter(o => o.id !== id))
  }

  const handleAddPurchaseOrder = () => {
    setPurchaseOrders([...purchaseOrders, { ...newPurchaseOrder, id: purchaseOrders.length + 1 }])
    setNewPurchaseOrder({ supplier: "", date: "", status: "", total: 0, items: [], paymentStatus: "", invoiceNumber: "" })
  }

  const handleEditPurchaseOrder = (purchaseOrder) => {
    setEditingPurchaseOrder(purchaseOrder)
  }

  

  const handleUpdatePurchaseOrder = () => {
    setPurchaseOrders(purchaseOrders.map(po => po.id === editingPurchaseOrder.id ? editingPurchaseOrder : po))
    setEditingPurchaseOrder(null)
  }

  const handleDeletePurchaseOrder = (id) => {
    setPurchaseOrders(purchaseOrders.filter(po => po.id !== id))
  }

  const handleAddEmployee = () => {
    setEmployees([...employees, { ...newEmployee, id: employees.length + 1 }])
    setNewEmployee({ name: "", position: "", department: "", email: "", phone: "", hireDate: "", salary: 0, performance: 0 })
  }

  const handleEditEmployee = (employee) => {
    setEditingEmployee(employee)
  }

  const handleUpdateEmployee = () => {
    setEmployees(employees.map(e => e.id === editingEmployee.id ? editingEmployee : e))
    setEditingEmployee(null)
  }

  const handleDeleteEmployee = (id) => {
    setEmployees(employees.filter(e => e.id !== id))
  }

  const handleAddTask = () => {
    setTasks([...tasks, { ...newTask, id: tasks.length + 1 }])
    setNewTask({ title: "", assignedTo: "", dueDate: "", status: "", priority: "" })
  }

  const handleEditTask = (task) => {
    setEditingTask(task)
  }

  const handleUpdateTask = () => {
    setTasks(tasks.map(t => t.id === editingTask.id ? editingTask : t))
    setEditingTask(null)
  }

  const handleDeleteTask = (id) => {
    setTasks(tasks.filter(t => t.id !== id))
  }

  const handleAddExpense = () => {
    setExpenses([...expenses, { ...newExpense, id: expenses.length + 1 }])
    setNewExpense({ category: "", amount: 0, date: "", approvedBy: "", paymentMethod: "" })
  }

  const handleEditExpense = (expense) => {
    setEditingExpense(expense)
  }

  const handleUpdateExpense = () => {
    setExpenses(expenses.map(e => e.id === editingExpense.id ? editingExpense : e))
    setEditingExpense(null)
  }

  const handleDeleteExpense = (id) => {
    setExpenses(expenses.filter(e => e.id !== id))
  }

  const warehouseLayout = Array(5).fill().map(() => Array(5).fill(null))
  products.forEach(product => {
    const [row, col] = product.location.split('')
    const rowIndex = row.charCodeAt(0) - 65
    const colIndex = parseInt(col) - 1
    if (rowIndex >= 0 && rowIndex < 5 && colIndex >= 0 && colIndex < 5) {
      warehouseLayout[rowIndex][colIndex] = product
    }
  })

  const stockData = products.map(product => ({
    name: product.name,
    actual: product.quantity,
    minimo: product.minStock,
    maximo: product.maxStock
  }))

  const salesData = [
    { name: 'Ene', ventas: 4000, costos: 3000 },
    { name: 'Feb', ventas: 3000, costos: 2500 },
    { name: 'Mar', ventas: 5000, costos: 4000 },
    { name: 'Abr', ventas: 4500, costos: 3500 },
    { name: 'May', ventas: 6000, costos: 4500 },
    { name: 'Jun', ventas: 5500, costos: 4000 },
  ]

  const topProducts = [
    { name: 'Producto A', value: 400 },
    { name: 'Producto B', value: 300 },
    { name: 'Producto C', value: 200 },
    { name: 'Producto D', value: 100 },
  ]

  const customerSegmentation = [
    { name: 'VIP', value: 30 },
    { name: 'Regular', value: 50 },
    { name: 'Ocasional', value: 20 },
  ]

  const supplierPerformance = suppliers.map(supplier => ({
    name: supplier.name,
    rating: supplier.rating,
    leadTime: supplier.leadTime,
  }))

  const employeePerformance = employees.map(employee => ({
    name: employee.name,
    performance: employee.performance,
  }))

  const COLORS = ['#0088FE', '#00C49F', '#FFBB28', '#FF8042', '#8884D8']

  return (
    <div className="flex h-screen bg-gray-100 dark:bg-gray-900">
      {/* Sidebar */}
      <aside className="w-64 bg-white dark:bg-gray-800 shadow-md">
        <div className="p-4">
          <h1 className="text-2xl font-bold text-gray-800 dark:text-white">ERP & WMS</h1>
        </div>
        <nav className="mt-4">
          <a
            href="#dashboard"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'dashboard' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('dashboard')}
          >
            <BarChart2 className="mr-3 h-5 w-5" />
            Dashboard
          </a>
          <a
            href="#inventory"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'inventory' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('inventory')}
          >
            <Package className="mr-3 h-5 w-5" />
            Inventario
          </a>
          <a
            href="#customers"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'customers' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('customers')}
          >
            <Users className="mr-3 h-5 w-5" />
            Clientes
          </a>
          <a
            href="#suppliers"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'suppliers' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('suppliers')}
          >
            <Truck className="mr-3 h-5 w-5" />
            Proveedores
          </a>
          <a
            href="#orders"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'orders' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('orders')}
          >
            <ShoppingCart className="mr-3 h-5 w-5" />
            Pedidos
          </a>
          <a
            href="#purchases"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'purchases' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('purchases')}
          >
            <DollarSign className="mr-3 h-5 w-5" />
            Compras
          </a>
          <a
            href="#warehouse"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'warehouse' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('warehouse')}
          >
            <Map className="mr-3 h-5 w-5" />
            Almacén
          </a>
          <a
            href="#employees"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'employees' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('employees')}
          >
            <Briefcase className="mr-3 h-5 w-5" />
            Empleados
          </a>
          <a
            href="#tasks"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'tasks' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('tasks')}
          >
            <Clipboard className="mr-3 h-5 w-5" />
            Tareas
          </a>
          <a
            href="#expenses"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'expenses' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('expenses')}
          >
            <FileText className="mr-3 h-5 w-5" />
            Gastos
          </a>
          <a
            href="#reports"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'reports' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('reports')}
          >
            <BarChart className="mr-3 h-5 w-5" />
            Informes
          </a>
          <a
            href="#settings"
            className={`flex items-center px-4 py-2 text-gray-700 dark:text-gray-200 ${activeTab === 'settings' ? 'bg-gray-200 dark:bg-gray-700' : ''}`}
            onClick={() => setActiveTab('settings')}
          >
            <Settings className="mr-3 h-5 w-5" />
            Configuración
          </a>
        </nav>
      </aside>

      {/* Main Content */}
      <main className="flex-1 overflow-x-hidden overflow-y-auto bg-gray-100 dark:bg-gray-900">
        <div className="container mx-auto px-6 py-8">
          <div className="flex items-center justify-between mb-4">
            <h3 className="text-gray-700 dark:text-white text-3xl font-medium">
              {activeTab === 'dashboard' && 'Dashboard'}
              {activeTab === 'inventory' && 'Gestión de Inventario'}
              {activeTab === 'customers' && 'Gestión de Clientes'}
              {activeTab === 'suppliers' && 'Gestión de Proveedores'}
              {activeTab === 'orders' && 'Gestión de Pedidos'}
              {activeTab === 'purchases' && 'Gestión de Compras'}
              {activeTab === 'warehouse' && 'Gestión de Almacén'}
              {activeTab === 'employees' && 'Gestión de Empleados'}
              {activeTab === 'tasks' && 'Gestión de Tareas'}
              {activeTab === 'expenses' && 'Gestión de Gastos'}
              {activeTab === 'reports' && 'Informes y Análisis'}
              {activeTab === 'settings' && 'Configuración del Sistema'}
            </h3>
            <div className="flex items-center">
              <div className="relative">
                <input
                  className="bg-gray-200 dark:bg-gray-700 text-gray-700 dark:text-white focus:outline-none focus:shadow-outline border border-gray-300 dark:border-gray-600 rounded-lg py-2 px-4 block w-full appearance-none leading-normal"
                  type="text"
                  placeholder="Buscar..."
                />
                <div className="absolute top-0 right-0 mt-2 mr-4">
                  <Search className="h-6 w-6 text-gray-500 dark:text-gray-400" />
                </div>
              </div>
              <button className="ml-4 bg-gray-200 dark:bg-gray-700 text-gray-700 dark:text-white py-2 px-4 rounded-lg">
                <Bell className="h-6 w-6" />
              </button>
              <button className="ml-4 bg-gray-200 dark:bg-gray-700 text-gray-700 dark:text-white py-2 px-4 rounded-lg">
                <HelpCircle className="h-6 w-6" />
              </button>
            </div>
          </div>

          {activeTab === 'dashboard' && (
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-8">
              <Card>
                <CardHeader>
                  <CardTitle>Resumen de Ventas y Costos</CardTitle>
                </CardHeader>
                <CardContent>
                  <ResponsiveContainer width="100%" height={300}>
                    <AreaChart data={salesData}>
                      <CartesianGrid strokeDasharray="3 3" />
                      <XAxis dataKey="name" />
                      <YAxis />
                      <Tooltip />
                      <Legend />
                      <Area type="monotone" dataKey="ventas" stroke="#8884d8" fill="#8884d8" />
                      <Area type="monotone" dataKey="costos" stroke="#82ca9d" fill="#82ca9d" />
                    </AreaChart>
                  </ResponsiveContainer>
                </CardContent>
              </Card>
              <Card>
                <CardHeader>
                  <CardTitle>Productos Más Vendidos</CardTitle>
                </CardHeader>
                <CardContent>
                  <ResponsiveContainer width="100%" height={300}>
                    <PieChart>
                      <Pie
                        data={topProducts}
                        cx="50%"
                        cy="50%"
                        labelLine={false}
                        outerRadius={80}
                        fill="#8884d8"
                        dataKey="value"
                      >
                        {topProducts.map((entry, index) => (
                          <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                        ))}
                      </Pie>
                      <Tooltip />
                      <Legend />
                    </PieChart>
                  </ResponsiveContainer>
                </CardContent>
              </Card>
              <Card>
                <CardHeader>
                  <CardTitle>KPIs</CardTitle>
                </CardHeader>
                <CardContent>
                  <div className="space-y-4">
                    <div>
                      <div className="flex justify-between mb-1">
                        <span>Ventas Mensuales</span>
                        <span>75%</span>
                      </div>
                      <Progress value={75} />
                    </div>
                    <div>
                      <div className="flex justify-between mb-1">
                        <span>Satisfacción del Cliente</span>
                        <span>90%</span>
                      </div>
                      <Progress value={90} />
                    </div>
                    <div>
                      <div className="flex justify-between mb-1">
                        <span>Eficiencia del Almacén</span>
                        <span>60%</span>
                      </div>
                      <Progress value={60} />
                    </div>
                    <div>
                      <div className="flex justify-between mb-1">
                        <span>Rotación de Inventario</span>
                        <span>80%</span>
                      </div>
                      <Progress value={80} />
                    </div>
                  </div>
                </CardContent>
              </Card>
              <Card>
                <CardHeader>
                  <CardTitle>Segmentación de Clientes</CardTitle>
                </CardHeader>
                <CardContent>
                  <ResponsiveContainer width="100%" height={300}>
                    <PieChart>
                      <Pie
                        data={customerSegmentation}
                        cx="50%"
                        cy="50%"
                        labelLine={false}
                        outerRadius={80}
                        fill="#8884d8"
                        dataKey="value"
                      >
                        {customerSegmentation.map((entry, index) => (
                          <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                        ))}
                      </Pie>
                      <Tooltip />
                      <Legend />
                    </PieChart>
                  </ResponsiveContainer>
                </CardContent>
              </Card>
              <Card>
                <CardHeader>
                  <CardTitle>Rendimiento de Proveedores</CardTitle>
                </CardHeader>
                <CardContent>
                  <ResponsiveContainer width="100%" height={300}>
                    <BarChart data={supplierPerformance}>
                      <CartesianGrid strokeDasharray="3 3" />
                      <XAxis dataKey="name" />
                      <YAxis yAxisId="left" orientation="left" stroke="#8884d8" />
                      <YAxis yAxisId="right" orientation="right" stroke="#82ca9d" />
                      <Tooltip />
                      <Legend />
                      <Bar yAxisId="left" dataKey="rating" fill="#8884d8" />
                      <Bar yAxisId="right" dataKey="leadTime" fill="#82ca9d" />
                    </BarChart>
                  </ResponsiveContainer>
                </CardContent>
              </Card>
              <Card>
                <CardHeader>
                  <CardTitle>Rendimiento de Empleados</CardTitle>
                </CardHeader>
                <CardContent>
                  <ResponsiveContainer width="100%" height={300}>
                    <BarChart data={employeePerformance}>
                      <CartesianGrid strokeDasharray="3 3" />
                      <XAxis dataKey="name" />
                      <YAxis />
                      <Tooltip />
                      <Legend />
                      <Bar dataKey="performance" fill="#8884d8" />
                    </BarChart>
                  </ResponsiveContainer>
                </CardContent>
              </Card>
            </div>
          )}

          {activeTab === 'inventory' && (
            <Card>
              <CardHeader>
                <CardTitle>Gestión de Inventario</CardTitle>
                <CardDescription>Añade, edita y elimina productos del inventario</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                  <Input
                    placeholder="Nombre del producto"
                    value={newProduct.name}
                    onChange={(e) => setNewProduct({ ...newProduct, name: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Cantidad"
                    value={newProduct.quantity}
                    onChange={(e) => setNewProduct({ ...newProduct, quantity: parseInt(e.target.value) })}
                  />
                  <Input
                    type="number"
                    placeholder="Precio"
                    value={newProduct.price}
                    onChange={(e) => setNewProduct({ ...newProduct, price: parseFloat(e.target.value) })}
                  />
                  <Input
                    type="number"
                    placeholder="Stock máximo"
                    value={newProduct.maxStock}
                    onChange={(e) => setNewProduct({ ...newProduct, maxStock: parseInt(e.target.value) })}
                  />
                  <Input
                    type="number"
                    placeholder="Stock mínimo"
                    value={newProduct.minStock}
                    onChange={(e) => setNewProduct({ ...newProduct, minStock: parseInt(e.target.value) })}
                  />
                  <Select
                    value={newProduct.level}
                    onValueChange={(value) => setNewProduct({ ...newProduct, level: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Nivel" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="A">A</SelectItem>
                      <SelectItem value="B">B</SelectItem>
                      <SelectItem value="C">C</SelectItem>
                    </SelectContent>
                  </Select>
                  <Input
                    placeholder="Ubicación (ej. A1)"
                    value={newProduct.location}
                    onChange={(e) => setNewProduct({ ...newProduct, location: e.target.value })}
                  />
                  <Input
                    placeholder="Proveedor"
                    value={newProduct.supplier}
                    onChange={(e) => setNewProduct({ ...newProduct, supplier: e.target.value })}
                  />
                  <Input
                    placeholder="Categoría"
                    value={newProduct.category}
                    onChange={(e) => setNewProduct({ ...newProduct, category: e.target.value })}
                  />
                  <Input
                    placeholder="SKU"
                    value={newProduct.sku}
                    onChange={(e) => setNewProduct({ ...newProduct, sku: e.target.value })}
                  />
                  <Input
                    placeholder="Código de barras"
                    value={newProduct.barcode}
                    onChange={(e) => setNewProduct({ ...newProduct, barcode: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Peso"
                    value={newProduct.weight}
                    onChange={(e) => setNewProduct({ ...newProduct, weight: parseFloat(e.target.value) })}
                  />
                  <Input
                    placeholder="Dimensiones"
                    value={newProduct.dimensions}
                    onChange={(e) => setNewProduct({ ...newProduct, dimensions: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Punto de reorden"
                    value={newProduct.reorderPoint}
                    onChange={(e) => setNewProduct({ ...newProduct, reorderPoint: parseInt(e.target.value) })}
                  />
                  <Input
                    type="date"
                    placeholder="Última reposición"
                    value={newProduct.lastRestocked}
                    onChange={(e) => setNewProduct({ ...newProduct, lastRestocked: e.target.value })}
                  />
                  <Input
                    type="date"
                    placeholder="Fecha de caducidad"
                    value={newProduct.expirationDate}
                    onChange={(e) => setNewProduct({ ...newProduct, expirationDate: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Costo"
                    value={newProduct.cost}
                    onChange={(e) => setNewProduct({ ...newProduct, cost: parseFloat(e.target.value) })}
                  />
                  <Input
                    type="number"
                    placeholder="Beneficio"
                    value={newProduct.profit}
                    onChange={(e) => setNewProduct({ ...newProduct, profit: parseFloat(e.target.value) })}
                  />
                  <Input
                    type="number"
                    placeholder="Velocidad de venta"
                    value={newProduct.salesVelocity}
                    onChange={(e) => setNewProduct({ ...newProduct, salesVelocity: parseFloat(e.target.value) })}
                  />
                </div>
                <Button onClick={handleAddProduct}>Añadir Producto</Button>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>Nombre</TableHead>
                      <TableHead>Cantidad</TableHead>
                      <TableHead>Precio</TableHead>
                      <TableHead>Stock Máx</TableHead>
                      <TableHead>Stock Mín</TableHead>
                      <TableHead>Nivel</TableHead>
                      <TableHead>Ubicación</TableHead>
                      <TableHead>Acciones</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    {products.map((product) => (
                      <TableRow key={product.id}>
                        <TableCell>{product.name}</TableCell>
                        <TableCell>{product.quantity}</TableCell>
                        <TableCell>${product.price}</TableCell>
                        <TableCell>{product.maxStock}</TableCell>
                        <TableCell>{product.minStock}</TableCell>
                        <TableCell>{product.level}</TableCell>
                        <TableCell>{product.location}</TableCell>
                        <TableCell>
                          <Dialog>
                            <DialogTrigger asChild>
                              <Button variant="outline" size="sm" onClick={() => handleEditProduct(product)}>
                                Editar
                              </Button>
                            </DialogTrigger>
                            <DialogContent>
                              <DialogHeader>
                                <DialogTitle>Editar Producto</DialogTitle>
                              </DialogHeader>
                              <div className="grid gap-4 py-4">
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="name" className="text-right">
                                    Nombre
                                  </Label>
                                  <Input
                                    id="name"
                                    value={editingProduct?.name}
                                    onChange={(e) =>
                                      setEditingProduct({ ...editingProduct, name: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="quantity" className="text-right">
                                    Cantidad
                                  </Label>
                                  <Input
                                    id="quantity"
                                    type="number"
                                    value={editingProduct?.quantity}
                                    onChange={(e) =>
                                      setEditingProduct({
                                        ...editingProduct,
                                        quantity: parseInt(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="price" className="text-right">
                                    Precio
                                  </Label>
                                  <Input
                                    id="price"
                                    type="number"
                                    value={editingProduct?.price}
                                    onChange={(e) =>
                                      setEditingProduct({
                                        ...editingProduct,
                                        price: parseFloat(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="maxStock" className="text-right">
                                    Stock Máximo
                                  </Label>
                                  <Input
                                    id="maxStock"
                                    type="number"
                                    value={editingProduct?.maxStock}
                                    onChange={(e) =>
                                      setEditingProduct({
                                        ...editingProduct,
                                        maxStock: parseInt(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="minStock" className="text-right">
                                    Stock Mínimo
                                  </Label>
                                  <Input
                                    id="minStock"
                                    type="number"
                                    value={editingProduct?.minStock}
                                    onChange={(e) =>
                                      setEditingProduct({
                                        ...editingProduct,
                                        minStock: parseInt(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="level" className="text-right">
                                    Nivel
                                  </Label>
                                  <Select
                                    value={editingProduct?.level}
                                    onValueChange={(value) =>
                                      setEditingProduct({ ...editingProduct, level: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="A">A</SelectItem>
                                      <SelectItem value="B">B</SelectItem>
                                      <SelectItem value="C">C</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="location" className="text-right">
                                    Ubicación
                                  </Label>
                                  <Input
                                    id="location"
                                    value={editingProduct?.location}
                                    onChange={(e) =>
                                      setEditingProduct({
                                        ...editingProduct,
                                        location: e.target.value,
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                              </div>
                              <Button onClick={handleUpdateProduct}>Guardar Cambios</Button>
                            </DialogContent>
                          </Dialog>
                          <AlertDialog>
                            <AlertDialogTrigger asChild>
                              <Button
                                variant="destructive"
                                size="sm"
                                className="ml-2"
                              >
                                Eliminar
                              </Button>
                            </AlertDialogTrigger>
                            <AlertDialogContent>
                              <AlertDialogHeader>
                                <AlertDialogTitle>¿Estás seguro?</AlertDialogTitle>
                                <AlertDialogDescription>
                                  Esta acción no se puede deshacer. Esto eliminará permanentemente el producto
                                  del inventario.
                                </AlertDialogDescription>
                              </AlertDialogHeader>
                              <AlertDialogFooter>
                                <AlertDialogCancel>Cancelar</AlertDialogCancel>
                                <AlertDialogAction onClick={() => handleDeleteProduct(product.id)}>
                                  Eliminar
                                </AlertDialogAction>
                              </AlertDialogFooter>
                            </AlertDialogContent>
                          </AlertDialog>
                        </TableCell>
                      </TableRow>
                    ))}
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          )}

          {activeTab === 'customers' && (
            <Card>
              <CardHeader>
                <CardTitle>Gestión de Clientes</CardTitle>
                <CardDescription>Añade, edita y elimina información de clientes</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                  <Input
                    placeholder="Nombre del cliente"
                    value={newCustomer.name}
                    onChange={(e) => setNewCustomer({ ...newCustomer, name: e.target.value })}
                  />
                  <Input
                    placeholder="Email del cliente"
                    value={newCustomer.email}
                    onChange={(e) => setNewCustomer({ ...newCustomer, email: e.target.value })}
                  />
                  <Input
                    placeholder="Teléfono"
                    value={newCustomer.phone}
                    onChange={(e) => setNewCustomer({ ...newCustomer, phone: e.target.value })}
                  />
                  <Input
                    placeholder="Dirección"
                    value={newCustomer.address}
                    onChange={(e) => setNewCustomer({ ...newCustomer, address: e.target.value })}
                  />
                  <Select
                    value={newCustomer.paymentMethod}
                    onValueChange={(value) => setNewCustomer({ ...newCustomer, paymentMethod: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Método de pago" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Tarjeta">Tarjeta</SelectItem>
                      <SelectItem value="Efectivo">Efectivo</SelectItem>
                      <SelectItem value="Transferencia">Transferencia</SelectItem>
                    </SelectContent>
                  </Select>
                  <Input
                    type="number"
                    placeholder="Límite de crédito"
                    value={newCustomer.creditLimit}
                    onChange={(e) => setNewCustomer({ ...newCustomer, creditLimit: parseFloat(e.target.value) })}
                  />
                  <Input
                    type="number"
                    placeholder="Saldo"
                    value={newCustomer.balance}
                    onChange={(e) => setNewCustomer({ ...newCustomer, balance: parseFloat(e.target.value) })}
                  />
                  <Input
                    type="date"
                    placeholder="Última compra"
                    value={newCustomer.lastPurchase}
                    onChange={(e) => setNewCustomer({ ...newCustomer, lastPurchase: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Puntos de fidelidad"
                    value={newCustomer.loyaltyPoints}
                    onChange={(e) => setNewCustomer({ ...newCustomer, loyaltyPoints: parseInt(e.target.value) })}
                  />
                  <Select
                    value={newCustomer.customerSegment}
                    onValueChange={(value) => setNewCustomer({ ...newCustomer, customerSegment: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Segmento de cliente" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="VIP">VIP</SelectItem>
                      <SelectItem value="Regular">Regular</SelectItem>
                      <SelectItem value="Ocasional">Ocasional</SelectItem>
                    </SelectContent>
                  </Select>
                </div>
                <Button onClick={handleAddCustomer}>Añadir Cliente</Button>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>Nombre</TableHead>
                      <TableHead>Email</TableHead>
                      <TableHead>Teléfono</TableHead>
                      <TableHead>Método de Pago</TableHead>
                      <TableHead>Límite de Crédito</TableHead>
                      <TableHead>Segmento</TableHead>
                      <TableHead>Acciones</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    {customers.map((customer) => (
                      <TableRow key={customer.id}>
                        <TableCell>{customer.name}</TableCell>
                        <TableCell>{customer.email}</TableCell>
                        <TableCell>{customer.phone}</TableCell>
                        <TableCell>{customer.paymentMethod}</TableCell>
                        <TableCell>${customer.creditLimit}</TableCell>
                        <TableCell>{customer.customerSegment}</TableCell>
                        <TableCell>
                          <Dialog>
                            <DialogTrigger asChild>
                              <Button variant="outline" size="sm" onClick={() => handleEditCustomer(customer)}>
                                Editar
                              </Button>
                            </DialogTrigger>
                            <DialogContent>
                              <DialogHeader>
                                <DialogTitle>Editar Cliente</DialogTitle>
                              </DialogHeader>
                              <div className="grid gap-4 py-4">
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="name" className="text-right">
                                    Nombre
                                  </Label>
                                  <Input
                                    id="name"
                                    value={editingCustomer?.name}
                                    onChange={(e) =>
                                      setEditingCustomer({ ...editingCustomer, name: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="email" className="text-right">
                                    Email
                                  </Label>
                                  <Input
                                    id="email"
                                    value={editingCustomer?.email}
                                    onChange={(e) =>
                                      setEditingCustomer({ ...editingCustomer, email: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="phone" className="text-right">
                                    Teléfono
                                  </Label>
                                  <Input
                                    id="phone"
                                    value={editingCustomer?.phone}
                                    onChange={(e) =>
                                      setEditingCustomer({ ...editingCustomer, phone: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="paymentMethod" className="text-right">
                                    Método de Pago
                                  </Label>
                                  <Select
                                    value={editingCustomer?.paymentMethod}
                                    onValueChange={(value) =>
                                      setEditingCustomer({ ...editingCustomer, paymentMethod: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="Tarjeta">Tarjeta</SelectItem>
                                      <SelectItem value="Efectivo">Efectivo</SelectItem>
                                      <SelectItem value="Transferencia">Transferencia</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="creditLimit" className="text-right">
                                    Límite de Crédito
                                  </Label>
                                  <Input
                                    id="creditLimit"
                                    type="number"
                                    value={editingCustomer?.creditLimit}
                                    onChange={(e) =>
                                      setEditingCustomer({
                                        ...editingCustomer,
                                        creditLimit: parseFloat(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="customerSegment" className="text-right">
                                    Segmento de Cliente
                                  </Label>
                                  <Select
                                    value={editingCustomer?.customerSegment}
                                    onValueChange={(value) =>
                                      setEditingCustomer({ ...editingCustomer, customerSegment: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="VIP">VIP</SelectItem>
                                      <SelectItem value="Regular">Regular</SelectItem>
                                      <SelectItem value="Ocasional">Ocasional</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                              </div>
                              <Button onClick={handleUpdateCustomer}>Guardar Cambios</Button>
                            </DialogContent>
                          </Dialog>
                          <AlertDialog>
                            <AlertDialogTrigger asChild>
                              <Button
                                variant="destructive"
                                size="sm"
                                className="ml-2"
                              >
                                Eliminar
                              </Button>
                            </AlertDialogTrigger>
                            <AlertDialogContent>
                              <AlertDialogHeader>
                                <AlertDialogTitle>¿Estás seguro?</AlertDialogTitle>
                                <AlertDialogDescription>
                                  Esta acción no se puede deshacer. Esto eliminará permanentemente al cliente
                                  y toda su información asociada.
                                </AlertDialogDescription>
                              </AlertDialogHeader>
                              <AlertDialogFooter>
                                <AlertDialogCancel>Cancelar</AlertDialogCancel>
                                <AlertDialogAction onClick={() => handleDeleteCustomer(customer.id)}>
                                  Eliminar
                                </AlertDialogAction>
                              </AlertDialogFooter>
                            </AlertDialogContent>
                          </AlertDialog>
                        </TableCell>
                      </TableRow>
                    ))}
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          )}

          {activeTab === 'suppliers' && (
            <Card>
              <CardHeader>
                <CardTitle>Gestión de Proveedores</CardTitle>
                <CardDescription>Añade, edita y elimina información de proveedores</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                  <Input
                    placeholder="Nombre del proveedor"
                    value={newSupplier.name}
                    onChange={(e) => setNewSupplier({ ...newSupplier, name: e.target.value })}
                  />
                  <Input
                    placeholder="Email del proveedor"
                    value={newSupplier.email}
                    onChange={(e) => setNewSupplier({ ...newSupplier, email: e.target.value })}
                  />
                  <Input
                    placeholder="Teléfono"
                    value={newSupplier.phone}
                    onChange={(e) => setNewSupplier({ ...newSupplier, phone: e.target.value })}
                  />
                  <Input
                    placeholder="Dirección"
                    value={newSupplier.address}
                    onChange={(e) => setNewSupplier({ ...newSupplier, address: e.target.value })}
                  />
                  <Input
                    placeholder="Términos de pago"
                    value={newSupplier.paymentTerms}
                    onChange={(e) => setNewSupplier({ ...newSupplier, paymentTerms: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Calificación"
                    value={newSupplier.rating}
                    onChange={(e) => setNewSupplier({ ...newSupplier, rating: parseFloat(e.target.value) })}
                  />
                  <Input
                    type="date"
                    placeholder="Último pedido"
                    value={newSupplier.lastOrder}
                    onChange={(e) => setNewSupplier({ ...newSupplier, lastOrder: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Tiempo de entrega (días)"
                    value={newSupplier.leadTime}
                    onChange={(e) => setNewSupplier({ ...newSupplier, leadTime: parseInt(e.target.value) })}
                  />
                  <Input
                    type="number"
                    placeholder="Cantidad mínima de pedido"
                    value={newSupplier.minimumOrderQuantity}
                    onChange={(e) => setNewSupplier({ ...newSupplier, minimumOrderQuantity: parseInt(e.target.value) })}
                  />
                  <Select
                    value={newSupplier.preferredShippingMethod}
                    onValueChange={(value) => setNewSupplier({ ...newSupplier, preferredShippingMethod: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Método de envío preferido" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Terrestre">Terrestre</SelectItem>
                      <SelectItem value="Aéreo">Aéreo</SelectItem>
                      <SelectItem value="Marítimo">Marítimo</SelectItem>
                    </SelectContent>
                  </Select>
                </div>
                <Button onClick={handleAddSupplier}>Añadir Proveedor</Button>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>Nombre</TableHead>
                      <TableHead>Email</TableHead>
                      <TableHead>Teléfono</TableHead>
                      <TableHead>Términos de Pago</TableHead>
                      <TableHead>Calificación</TableHead>
                      <TableHead>Tiempo de Entrega</TableHead>
                      <TableHead>Acciones</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    {suppliers.map((supplier) => (
                      <TableRow key={supplier.id}>
                        <TableCell>{supplier.name}</TableCell>
                        <TableCell>{supplier.email}</TableCell>
                        <TableCell>{supplier.phone}</TableCell>
                        <TableCell>{supplier.paymentTerms}</TableCell>
                        <TableCell>{supplier.rating}</TableCell>
                        <TableCell>{supplier.leadTime} días</TableCell>
                        <TableCell>
                          <Dialog>
                            <DialogTrigger asChild>
                              <Button variant="outline" size="sm" onClick={() => handleEditSupplier(supplier)}>
                                Editar
                              </Button>
                            </DialogTrigger>
                            <DialogContent>
                              <DialogHeader>
                                <DialogTitle>Editar Proveedor</DialogTitle>
                              </DialogHeader>
                              <div className="grid gap-4 py-4">
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="name" className="text-right">
                                    Nombre
                                  </Label>
                                  <Input
                                    id="name"
                                    value={editingSupplier?.name}
                                    onChange={(e) =>
                                      setEditingSupplier({ ...editingSupplier, name: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="email" className="text-right">
                                    Email
                                  </Label>
                                  <Input
                                    id="email"
                                    value={editingSupplier?.email}
                                    onChange={(e) =>
                                      setEditingSupplier({ ...editingSupplier, email: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="phone" className="text-right">
                                    Teléfono
                                  </Label>
                                  <Input
                                    id="phone"
                                    value={editingSupplier?.phone}
                                    onChange={(e) =>
                                      setEditingSupplier({ ...editingSupplier, phone: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="paymentTerms" className="text-right">
                                    Términos de Pago
                                  </Label>
                                  <Input
                                    id="paymentTerms"
                                    value={editingSupplier?.paymentTerms}
                                    onChange={(e) =>
                                      setEditingSupplier({ ...editingSupplier, paymentTerms: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="rating" className="text-right">
                                    Calificación
                                  </Label>
                                  <Input
                                    id="rating"
                                    type="number"
                                    value={editingSupplier?.rating}
                                    onChange={(e) =>
                                      setEditingSupplier({
                                        ...editingSupplier,
                                        rating: parseFloat(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="leadTime" className="text-right">
                                    Tiempo de Entrega
                                  </Label>
                                  <Input
                                    id="leadTime"
                                    type="number"
                                    value={editingSupplier?.leadTime}
                                    onChange={(e) =>
                                      setEditingSupplier({
                                        ...editingSupplier,
                                        leadTime: parseInt(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                              </div>
                              <Button onClick={handleUpdateSupplier}>Guardar Cambios</Button>
                            </DialogContent>
                          </Dialog>
                          <AlertDialog>
                            <AlertDialogTrigger asChild>
                              <Button
                                variant="destructive"
                                size="sm"
                                className="ml-2"
                              >
                                Eliminar
                              </Button>
                            </AlertDialogTrigger>
                            <AlertDialogContent>
                              <AlertDialogHeader>
                                <AlertDialogTitle>¿Estás seguro?</AlertDialogTitle>
                                <AlertDialogDescription>
                                  Esta acción no se puede deshacer. Esto eliminará permanentemente al proveedor
                                  y toda su información asociada.
                                </AlertDialogDescription>
                              </AlertDialogHeader>
                              <AlertDialogFooter>
                                <AlertDialogCancel>Cancelar</AlertDialogCancel>
                                <AlertDialogAction onClick={() => handleDeleteSupplier(supplier.id)}>
                                  Eliminar
                                </AlertDialogAction>
                              </AlertDialogFooter>
                            </AlertDialogContent>
                          </AlertDialog>
                        </TableCell>
                      </TableRow>
                    ))}
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          )}

          {activeTab === 'orders' && (
            <Card>
              <CardHeader>
                <CardTitle>Gestión de Pedidos</CardTitle>
                <CardDescription>Añade, edita y elimina pedidos de clientes</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                  <Select
                    value={newOrder.customer}
                    onValueChange={(value) => setNewOrder({ ...newOrder, customer: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Cliente" />
                    </SelectTrigger>
                    <SelectContent>
                      {customers.map((customer) => (
                        <SelectItem key={customer.id} value={customer.name}>
                          {customer.name}
                        </SelectItem>
                      ))}
                    </SelectContent>
                  </Select>
                  <Input
                    type="date"
                    value={newOrder.date}
                    onChange={(e) => setNewOrder({ ...newOrder, date: e.target.value })}
                  />
                  <Select
                    value={newOrder.status}
                    onValueChange={(value) => setNewOrder({ ...newOrder, status: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Estado" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Pendiente">Pendiente</SelectItem>
                      <SelectItem value="En proceso">En proceso</SelectItem>
                      <SelectItem value="Enviado">Enviado</SelectItem>
                      <SelectItem value="Entregado">Entregado</SelectItem>
                    </SelectContent>
                  </Select>
                  <Input
                    type="number"
                    placeholder="Total"
                    value={newOrder.total}
                    onChange={(e) => setNewOrder({ ...newOrder, total: parseFloat(e.target.value) })}
                  />
                  <Select
                    value={newOrder.shippingMethod}
                    onValueChange={(value) => setNewOrder({ ...newOrder, shippingMethod: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Método de envío" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Estándar">Estándar</SelectItem>
                      <SelectItem value="Express">Express</SelectItem>
                      <SelectItem value="Urgente">Urgente</SelectItem>
                    </SelectContent>
                  </Select>
                  <Input
                    placeholder="Número de seguimiento"
                    value={newOrder.trackingNumber}
                    onChange={(e) => setNewOrder({ ...newOrder, trackingNumber: e.target.value })}
                  />
                  <Input
                    type="date"
                    placeholder="Entrega estimada"
                    value={newOrder.estimatedDelivery}
                    onChange={(e) => setNewOrder({ ...newOrder, estimatedDelivery: e.target.value })}
                  />
                </div>
                <Button onClick={handleAddOrder}>Añadir Pedido</Button>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>Cliente</TableHead>
                      <TableHead>Fecha</TableHead>
                      <TableHead>Estado</TableHead>
                      <TableHead>Total</TableHead>
                      <TableHead>Método de Envío</TableHead>
                      <TableHead>Entrega Estimada</TableHead>
                      <TableHead>Acciones</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    {orders.map((order) => (
                      <TableRow key={order.id}>
                        <TableCell>{order.customer}</TableCell>
                        <TableCell>{order.date}</TableCell>
                        <TableCell>{order.status}</TableCell>
                        <TableCell>${order.total}</TableCell>
                        <TableCell>{order.shippingMethod}</TableCell>
                        <TableCell>{order.estimatedDelivery}</TableCell>
                        <TableCell>
                          <Dialog>
                            <DialogTrigger asChild>
                              <Button variant="outline" size="sm" onClick={() => handleEditOrder(order)}>
                                Editar
                              </Button>
                            </DialogTrigger>
                            <DialogContent>
                              <DialogHeader>
                                <DialogTitle>Editar Pedido</DialogTitle>
                              </DialogHeader>
                              <div className="grid gap-4 py-4">
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="customer" className="text-right">
                                    Cliente
                                  </Label>
                                  <Select
                                    value={editingOrder?.customer}
                                    onValueChange={(value) =>
                                      setEditingOrder({ ...editingOrder, customer: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      {customers.map((customer) => (
                                        <SelectItem key={customer.id} value={customer.name}>
                                          {customer.name}
                                        </SelectItem>
                                      ))}
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="date" className="text-right">
                                    Fecha
                                  </Label>
                                  <Input
                                    id="date"
                                    type="date"
                                    value={editingOrder?.date}
                                    onChange={(e) =>
                                      setEditingOrder({ ...editingOrder, date: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="status" className="text-right">
                                    Estado
                                  </Label>
                                  <Select
                                    value={editingOrder?.status}
                                    onValueChange={(value) =>
                                      setEditingOrder({ ...editingOrder, status: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="Pendiente">Pendiente</SelectItem>
                                      <SelectItem value="En proceso">En proceso</SelectItem>
                                      <SelectItem value="Enviado">Enviado</SelectItem>
                                      <SelectItem value="Entregado">Entregado</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="total" className="text-right">
                                    Total
                                  </Label>
                                  <Input
                                    id="total"
                                    type="number"
                                    value={editingOrder?.total}
                                    onChange={(e) =>
                                      setEditingOrder({
                                        ...editingOrder,
                                        total: parseFloat(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="shippingMethod" className="text-right">
                                    Método de Envío
                                  </Label>
                                  <Select
                                    value={editingOrder?.shippingMethod}
                                    onValueChange={(value) =>
                                      setEditingOrder({ ...editingOrder, shippingMethod: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="Estándar">Estándar</SelectItem>
                                      <SelectItem value="Express">Express</SelectItem>
                                      <SelectItem value="Urgente">Urgente</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="estimatedDelivery" className="text-right">
                                    Entrega Estimada
                                  </Label>
                                  <Input
                                    id="estimatedDelivery"
                                    type="date"
                                    value={editingOrder?.estimatedDelivery}
                                    onChange={(e) =>
                                      setEditingOrder({
                                        ...editingOrder,
                                        estimatedDelivery: e.target.value,
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                              </div>
                              <Button onClick={handleUpdateOrder}>Guardar Cambios</Button>
                            </DialogContent>
                          </Dialog>
                          <AlertDialog>
                            <AlertDialogTrigger asChild>
                              <Button
                                variant="destructive"
                                size="sm"
                                className="ml-2"
                              >
                                Eliminar
                              </Button>
                            </AlertDialogTrigger>
                            <AlertDialogContent>
                              <AlertDialogHeader>
                                <AlertDialogTitle>¿Estás seguro?</AlertDialogTitle>
                                <AlertDialogDescription>
                                  Esta acción no se puede deshacer. Esto eliminará permanentemente el pedido
                                  y toda su información asociada.
                                </AlertDialogDescription>
                              </AlertDialogHeader>
                              <AlertDialogFooter>
                                <AlertDialogCancel>Cancelar</AlertDialogCancel>
                                <AlertDialogAction onClick={() => handleDeleteOrder(order.id)}>
                                  Eliminar
                                </AlertDialogAction>
                              </AlertDialogFooter>
                            </AlertDialogContent>
                          </AlertDialog>
                        </TableCell>
                      </TableRow>
                    ))}
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          )}

          {activeTab === 'purchases' && (
            <Card>
              <CardHeader>
                <CardTitle>Gestión de Compras</CardTitle>
                <CardDescription>Añade, edita y elimina órdenes de compra a proveedores</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                  <Select
                    value={newPurchaseOrder.supplier}
                    onValueChange={(value) => setNewPurchaseOrder({ ...newPurchaseOrder, supplier: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Proveedor" />
                    </SelectTrigger>
                    <SelectContent>
                      {suppliers.map((supplier) => (
                        <SelectItem key={supplier.id} value={supplier.name}>
                          {supplier.name}
                        </SelectItem>
                      ))}
                    </SelectContent>
                  </Select>
                  <Input
                    type="date"
                    value={newPurchaseOrder.date}
                    onChange={(e) => setNewPurchaseOrder({ ...newPurchaseOrder, date: e.target.value })}
                  />
                  <Select
                    value={newPurchaseOrder.status}
                    onValueChange={(value) => setNewPurchaseOrder({ ...newPurchaseOrder, status: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Estado" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Pendiente">Pendiente</SelectItem>
                      <SelectItem value="En proceso">En proceso</SelectItem>
                      <SelectItem value="Recibido">Recibido</SelectItem>
                    </SelectContent>
                  </Select>
                  <Input
                    type="number"
                    placeholder="Total"
                    value={newPurchaseOrder.total}
                    onChange={(e) => setNewPurchaseOrder({ ...newPurchaseOrder, total: parseFloat(e.target.value) })}
                  />
                  <Select
                    value={newPurchaseOrder.paymentStatus}
                    onValueChange={(value) => setNewPurchaseOrder({ ...newPurchaseOrder, paymentStatus: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Estado de pago" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Pendiente">Pendiente</SelectItem>
                      <SelectItem value="Pagado">Pagado</SelectItem>
                      <SelectItem value="Parcial">Parcial</SelectItem>
                    </SelectContent>
                  </Select>
                  <Input
                    placeholder="Número de factura"
                    value={newPurchaseOrder.invoiceNumber}
                    onChange={(e) => setNewPurchaseOrder({ ...newPurchaseOrder, invoiceNumber: e.target.value })}
                  />
                </div>
                <Button onClick={handleAddPurchaseOrder}>Añadir Orden de Compra</Button>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>Proveedor</TableHead>
                      <TableHead>Fecha</TableHead>
                      <TableHead>Estado</TableHead>
                      <TableHead>Total</TableHead>
                      <TableHead>Estado de Pago</TableHead>
                      <TableHead>Número de Factura</TableHead>
                      <TableHead>Acciones</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    {purchaseOrders.map((purchaseOrder) => (
                      <TableRow key={purchaseOrder.id}>
                        <TableCell>{purchaseOrder.supplier}</TableCell>
                        <TableCell>{purchaseOrder.date}</TableCell>
                        <TableCell>{purchaseOrder.status}</TableCell>
                        <TableCell>${purchaseOrder.total}</TableCell>
                        <TableCell>{purchaseOrder.paymentStatus}</TableCell>
                        <TableCell>{purchaseOrder.invoiceNumber}</TableCell>
                        <TableCell>
                          <Dialog>
                            <DialogTrigger asChild>
                              <Button variant="outline" size="sm" onClick={() => handleEditPurchaseOrder(purchaseOrder)}>
                                Editar
                              </Button>
                            </DialogTrigger>
                            <DialogContent>
                              <DialogHeader>
                                <DialogTitle>Editar Orden de Compra</DialogTitle>
                              </DialogHeader>
                              <div className="grid gap-4 py-4">
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="supplier" className="text-right">
                                    Proveedor
                                  </Label>
                                  <Select
                                    value={editingPurchaseOrder?.supplier}
                                    onValueChange={(value) =>
                                      setEditingPurchaseOrder({ ...editingPurchaseOrder, supplier: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      {suppliers.map((supplier) => (
                                        <SelectItem key={supplier.id} value={supplier.name}>
                                          {supplier.name}
                                        </SelectItem>
                                      ))}
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="date" className="text-right">
                                    Fecha
                                  </Label>
                                  <Input
                                    id="date"
                                    type="date"
                                    value={editingPurchaseOrder?.date}
                                    onChange={(e) =>
                                      setEditingPurchaseOrder({ ...editingPurchaseOrder, date: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="status" className="text-right">
                                    Estado
                                  </Label>
                                  <Select
                                    value={editingPurchaseOrder?.status}
                                    onValueChange={(value) =>
                                      setEditingPurchaseOrder({ ...editingPurchaseOrder, status: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="Pendiente">Pendiente</SelectItem>
                                      <SelectItem value="En proceso">En proceso</SelectItem>
                                      <SelectItem value="Recibido">Recibido</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="total" className="text-right">
                                    Total
                                  </Label>
                                  <Input
                                    id="total"
                                    type="number"
                                    value={editingPurchaseOrder?.total}
                                    onChange={(e) =>
                                      setEditingPurchaseOrder({
                                        ...editingPurchaseOrder,
                                        total: parseFloat(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="paymentStatus" className="text-right">
                                    Estado de Pago
                                  </Label>
                                  <Select
                                    value={editingPurchaseOrder?.paymentStatus}
                                    onValueChange={(value) =>
                                      setEditingPurchaseOrder({ ...editingPurchaseOrder, paymentStatus: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="Pendiente">Pendiente</SelectItem>
                                      <SelectItem value="Pagado">Pagado</SelectItem>
                                      <SelectItem value="Parcial">Parcial</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="invoiceNumber" className="text-right">
                                    Número de Factura
                                  </Label>
                                  <Input
                                    id="invoiceNumber"
                                    value={editingPurchaseOrder?.invoiceNumber}
                                    onChange={(e) =>
                                      setEditingPurchaseOrder({
                                        ...editingPurchaseOrder,
                                        invoiceNumber: e.target.value,
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                              </div>
                              <Button onClick={handleUpdatePurchaseOrder}>Guardar Cambios</Button>
                            </DialogContent>
                          </Dialog>
                          <AlertDialog>
                            <AlertDialogTrigger asChild>
                              <Button
                                variant="destructive"
                                size="sm"
                                className="ml-2"
                              >
                                Eliminar
                              </Button>
                            </AlertDialogTrigger>
                            <AlertDialogContent>
                              <AlertDialogHeader>
                                <AlertDialogTitle>¿Estás seguro?</AlertDialogTitle>
                                <AlertDialogDescription>
                                  Esta acción no se puede deshacer. Esto eliminará permanentemente la orden de compra
                                  y toda su información asociada.
                                </AlertDialogDescription>
                              </AlertDialogHeader>
                              <AlertDialogFooter>
                                <AlertDialogCancel>Cancelar</AlertDialogCancel>
                                <AlertDialogAction onClick={() => handleDeletePurchaseOrder(purchaseOrder.id)}>
                                  Eliminar
                                </AlertDialogAction>
                              </AlertDialogFooter>
                            </AlertDialogContent>
                          </AlertDialog>
                        </TableCell>
                      </TableRow>
                    ))}
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          )}

          {activeTab === 'warehouse' && (
            <Card>
              <CardHeader>
                <CardTitle>Diseño del Almacén</CardTitle>
                <CardDescription>Vista gráfica de la disposición del almacén</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-5 gap-2">
                  {warehouseLayout.map((row, rowIndex) =>
                    row.map((cell, colIndex) => (
                      <div
                        key={`${rowIndex}-${colIndex}`}
                        className={`p-2 border ${
                          cell ? "bg-blue-200 dark:bg-blue-800" : "bg-gray-100 dark:bg-gray-700"
                        } text-center cursor-pointer`}
                        onClick={() => {
                          if (cell) {
                            alert(`Producto: ${cell.name}
Cantidad: ${cell.quantity}
Ubicación: ${cell.location}`)
                          }
                        }}
                      >
                        {String.fromCharCode(65 + rowIndex)}
                        {colIndex + 1}
                      </div>
                    ))
                  )}
                </div>
              </CardContent>
            </Card>
          )}

          {activeTab === 'employees' && (
            <Card>
              <CardHeader>
                <CardTitle>Gestión de Empleados</CardTitle>
                <CardDescription>Añade, edita y elimina información de empleados</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                  <Input
                    placeholder="Nombre del empleado"
                    value={newEmployee.name}
                    onChange={(e) => setNewEmployee({ ...newEmployee, name: e.target.value })}
                  />
                  <Input
                    placeholder="Posición"
                    value={newEmployee.position}
                    onChange={(e) => setNewEmployee({ ...newEmployee, position: e.target.value })}
                  />
                  <Input
                    placeholder="Departamento"
                    value={newEmployee.department}
                    onChange={(e) => setNewEmployee({ ...newEmployee, department: e.target.value })}
                  />
                  <Input
                    placeholder="Email"
                    value={newEmployee.email}
                    onChange={(e) => setNewEmployee({ ...newEmployee, email: e.target.value })}
                  />
                  <Input
                    placeholder="Teléfono"
                    value={newEmployee.phone}
                    onChange={(e) => setNewEmployee({ ...newEmployee, phone: e.target.value })}
                  />
                  <Input
                    type="date"
                    placeholder="Fecha de contratación"
                    value={newEmployee.hireDate}
                    onChange={(e) => setNewEmployee({ ...newEmployee, hireDate: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Salario"
                    value={newEmployee.salary}
                    onChange={(e) => setNewEmployee({ ...newEmployee, salary: parseFloat(e.target.value) })}
                  />
                  <Input
                    type="number"
                    placeholder="Rendimiento"
                    value={newEmployee.performance}
                    onChange={(e) => setNewEmployee({ ...newEmployee, performance: parseFloat(e.target.value) })}
                  />
                </div>
                <Button onClick={handleAddEmployee}>Añadir Empleado</Button>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>Nombre</TableHead>
                      <TableHead>Posición</TableHead>
                      <TableHead>Departamento</TableHead>
                      <TableHead>Email</TableHead>
                      <TableHead>Fecha de Contratación</TableHead>
                      <TableHead>Rendimiento</TableHead>
                      <TableHead>Acciones</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    {employees.map((employee) => (
                      <TableRow key={employee.id}>
                        <TableCell>{employee.name}</TableCell>
                        <TableCell>{employee.position}</TableCell>
                        <TableCell>{employee.department}</TableCell>
                        <TableCell>{employee.email}</TableCell>
                        <TableCell>{employee.hireDate}</TableCell>
                        <TableCell>{employee.performance}</TableCell>
                        <TableCell>
                          <Dialog>
                            <DialogTrigger asChild>
                              <Button variant="outline" size="sm" onClick={() => handleEditEmployee(employee)}>
                                Editar
                              </Button>
                            </DialogTrigger>
                            <DialogContent>
                              <DialogHeader>
                                <DialogTitle>Editar Empleado</DialogTitle>
                              </DialogHeader>
                              <div className="grid gap-4 py-4">
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="name" className="text-right">
                                    Nombre
                                  </Label>
                                  <Input
                                    id="name"
                                    value={editingEmployee?.name}
                                    onChange={(e) =>
                                      setEditingEmployee({ ...editingEmployee, name: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="position" className="text-right">
                                    Posición
                                  </Label>
                                  <Input
                                    id="position"
                                    value={editingEmployee?.position}
                                    onChange={(e) =>
                                      setEditingEmployee({ ...editingEmployee, position: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="department" className="text-right">
                                    Departamento
                                  </Label>
                                  <Input
                                    id="department"
                                    value={editingEmployee?.department}
                                    onChange={(e) =>
                                      setEditingEmployee({ ...editingEmployee, department: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="email" className="text-right">
                                    Email
                                  </Label>
                                  <Input
                                    id="email"
                                    value={editingEmployee?.email}
                                    onChange={(e) =>
                                      setEditingEmployee({ ...editingEmployee, email: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="hireDate" className="text-right">
                                    Fecha de Contratación
                                  </Label>
                                  <Input
                                    id="hireDate"
                                    type="date"
                                    value={editingEmployee?.hireDate}
                                    onChange={(e) =>
                                      setEditingEmployee({ ...editingEmployee, hireDate: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="performance" className="text-right">
                                    Rendimiento
                                  </Label>
                                  <Input
                                    id="performance"
                                    type="number"
                                    value={editingEmployee?.performance}
                                    onChange={(e) =>
                                      setEditingEmployee({
                                        ...editingEmployee,
                                        performance: parseFloat(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                              </div>
                              <Button onClick={handleUpdateEmployee}>Guardar Cambios</Button>
                            </DialogContent>
                          </Dialog>
                          <AlertDialog>
                            <AlertDialogTrigger asChild>
                              <Button
                                variant="destructive"
                                size="sm"
                                className="ml-2"
                              >
                                Eliminar
                              </Button>
                            </AlertDialogTrigger>
                            <AlertDialogContent>
                              <AlertDialogHeader>
                                <AlertDialogTitle>¿Estás seguro?</AlertDialogTitle>
                                <AlertDialogDescription>
                                  Esta acción no se puede deshacer. Esto eliminará permanentemente al empleado
                                  y toda su información asociada.
                                </AlertDialogDescription>
                              </AlertDialogHeader>
                              <AlertDialogFooter>
                                <AlertDialogCancel>Cancelar</AlertDialogCancel>
                                <AlertDialogAction onClick={() => handleDeleteEmployee(employee.id)}>
                                  Eliminar
                                </AlertDialogAction>
                              </AlertDialogFooter>
                            </AlertDialogContent>
                          </AlertDialog>
                        </TableCell>
                      </TableRow>
                    ))}
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          )}

          {activeTab === 'tasks' && (
            <Card>
              <CardHeader>
                <CardTitle>Gestión de Tareas</CardTitle>
                <CardDescription>Añade, edita y elimina tareas</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                  <Input
                    placeholder="Título de la tarea"
                    value={newTask.title}
                    onChange={(e) => setNewTask({ ...newTask, title: e.target.value })}
                  />
                  <Select
                    value={newTask.assignedTo}
                    onValueChange={(value) => setNewTask({ ...newTask, assignedTo: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Asignado a" />
                    </SelectTrigger>
                    <SelectContent>
                      {employees.map((employee) => (
                        <SelectItem key={employee.id} value={employee.name}>
                          {employee.name}
                        </SelectItem>
                      ))}
                    </SelectContent>
                  </Select>
                  <Input
                    type="date"
                    placeholder="Fecha de vencimiento"
                    value={newTask.dueDate}
                    onChange={(e) => setNewTask({ ...newTask, dueDate: e.target.value })}
                  />
                  <Select
                    value={newTask.status}
                    onValueChange={(value) => setNewTask({ ...newTask, status: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Estado" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Pendiente">Pendiente</SelectItem>
                      <SelectItem value="En progreso">En progreso</SelectItem>
                      <SelectItem value="Completada">Completada</SelectItem>
                    </SelectContent>
                  </Select>
                  <Select
                    value={newTask.priority}
                    onValueChange={(value) => setNewTask({ ...newTask, priority: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Prioridad" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Baja">Baja</SelectItem>
                      <SelectItem value="Media">Media</SelectItem>
                      <SelectItem value="Alta">Alta</SelectItem>
                    </SelectContent>
                  </Select>
                </div>
                <Button onClick={handleAddTask}>Añadir Tarea</Button>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>Título</TableHead>
                      <TableHead>Asignado a</TableHead>
                      <TableHead>Fecha de Vencimiento</TableHead>
                      <TableHead>Estado</TableHead>
                      <TableHead>Prioridad</TableHead>
                      <TableHead>Acciones</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    {tasks.map((task) => (
                      <TableRow key={task.id}>
                        <TableCell>{task.title}</TableCell>
                        <TableCell>{task.assignedTo}</TableCell>
                        <TableCell>{task.dueDate}</TableCell>
                        <TableCell>{task.status}</TableCell>
                        <TableCell>{task.priority}</TableCell>
                        <TableCell>
                          <Dialog>
                            <DialogTrigger asChild>
                              <Button variant="outline" size="sm" onClick={() => handleEditTask(task)}>
                                Editar
                              </Button>
                            </DialogTrigger>
                            <DialogContent>
                              <DialogHeader>
                                <DialogTitle>Editar Tarea</DialogTitle>
                              </DialogHeader>
                              <div className="grid gap-4 py-4">
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="title" className="text-right">
                                    Título
                                  </Label>
                                  <Input
                                    id="title"
                                    value={editingTask?.title}
                                    onChange={(e) =>
                                      setEditingTask({ ...editingTask, title: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="assignedTo" className="text-right">
                                    Asignado a
                                  </Label>
                                  <Select
                                    value={editingTask?.assignedTo}
                                    onValueChange={(value) =>
                                      setEditingTask({ ...editingTask, assignedTo: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      {employees.map((employee) => (
                                        <SelectItem key={employee.id} value={employee.name}>
                                          {employee.name}
                                        </SelectItem>
                                      ))}
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="dueDate" className="text-right">
                                    Fecha de Vencimiento
                                  </Label>
                                  <Input
                                    id="dueDate"
                                    type="date"
                                    value={editingTask?.dueDate}
                                    onChange={(e) =>
                                      setEditingTask({ ...editingTask, dueDate: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="status" className="text-right">
                                    Estado
                                  </Label>
                                  <Select
                                    value={editingTask?.status}
                                    onValueChange={(value) =>
                                      setEditingTask({ ...editingTask, status: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="Pendiente">Pendiente</SelectItem>
                                      <SelectItem value="En progreso">En progreso</SelectItem>
                                      <SelectItem value="Completada">Completada</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="priority" className="text-right">
                                    Prioridad
                                  </Label>
                                  <Select
                                    value={editingTask?.priority}
                                    onValueChange={(value) =>
                                      setEditingTask({ ...editingTask, priority: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="Baja">Baja</SelectItem>
                                      <SelectItem value="Media">Media</SelectItem>
                                      <SelectItem value="Alta">Alta</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                              </div>
                              <Button onClick={handleUpdateTask}>Guardar Cambios</Button>
                            </DialogContent>
                          </Dialog>
                          <AlertDialog>
                            <AlertDialogTrigger asChild>
                              <Button
                                variant="destructive"
                                size="sm"
                                className="ml-2"
                              >
                                Eliminar
                              </Button>
                            </AlertDialogTrigger>
                            <AlertDialogContent>
                              <AlertDialogHeader>
                                <AlertDialogTitle>¿Estás seguro?</AlertDialogTitle>
                                <AlertDialogDescription>
                                  Esta acción no se puede deshacer. Esto eliminará permanentemente la tarea.
                                </AlertDialogDescription>
                              </AlertDialogHeader>
                              <AlertDialogFooter>
                                <AlertDialogCancel>Cancelar</AlertDialogCancel>
                                <AlertDialogAction onClick={() => handleDeleteTask(task.id)}>
                                  Eliminar
                                </AlertDialogAction>
                              </AlertDialogFooter>
                            </AlertDialogContent>
                          </AlertDialog>
                        </TableCell>
                      </TableRow>
                    ))}
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          )}

          {activeTab === 'expenses' && (
            <Card>
              <CardHeader>
                <CardTitle>Gestión de Gastos</CardTitle>
                <CardDescription>Añade, edita y elimina gastos</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                  <Input
                    placeholder="Categoría"
                    value={newExpense.category}
                    onChange={(e) => setNewExpense({ ...newExpense, category: e.target.value })}
                  />
                  <Input
                    type="number"
                    placeholder="Monto"
                    value={newExpense.amount}
                    onChange={(e) => setNewExpense({ ...newExpense, amount: parseFloat(e.target.value) })}
                  />
                  <Input
                    type="date"
                    placeholder="Fecha"
                    value={newExpense.date}
                    onChange={(e) => setNewExpense({ ...newExpense, date: e.target.value })}
                  />
                  <Select
                    value={newExpense.approvedBy}
                    onValueChange={(value) => setNewExpense({ ...newExpense, approvedBy: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Aprobado por" />
                    </SelectTrigger>
                    <SelectContent>
                      {employees.map((employee) => (
                        <SelectItem key={employee.id} value={employee.name}>
                          {employee.name}
                        </SelectItem>
                      ))}
                    </SelectContent>
                  </Select>
                  <Select
                    value={newExpense.paymentMethod}
                    onValueChange={(value) => setNewExpense({ ...newExpense, paymentMethod: value })}
                  >
                    <SelectTrigger>
                      <SelectValue placeholder="Método de pago" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="Efectivo">Efectivo</SelectItem>
                      <SelectItem value="Tarjeta de crédito">Tarjeta de crédito</SelectItem>
                      <SelectItem value="Transferencia bancaria">Transferencia bancaria</SelectItem>
                    </SelectContent>
                  </Select>
                </div>
                <Button onClick={handleAddExpense}>Añadir Gasto</Button>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>Categoría</TableHead>
                      <TableHead>Monto</TableHead>
                      <TableHead>Fecha</TableHead>
                      <TableHead>Aprobado por</TableHead>
                      <TableHead>Método de Pago</TableHead>
                      <TableHead>Acciones</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    {expenses.map((expense) => (
                      <TableRow key={expense.id}>
                        <TableCell>{expense.category}</TableCell>
                        <TableCell>${expense.amount}</TableCell>
                        <TableCell>{expense.date}</TableCell>
                        <TableCell>{expense.approvedBy}</TableCell>
                        <TableCell>{expense.paymentMethod}</TableCell>
                        <TableCell>
                          <Dialog>
                            <DialogTrigger asChild>
                              <Button variant="outline" size="sm" onClick={() => handleEditExpense(expense)}>
                                Editar
                              </Button>
                            </DialogTrigger>
                            <DialogContent>
                              <DialogHeader>
                                <DialogTitle>Editar Gasto</DialogTitle>
                              </DialogHeader>
                              <div className="grid gap-4 py-4">
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="category" className="text-right">
                                    Categoría
                                  </Label>
                                  <Input
                                    id="category"
                                    value={editingExpense?.category}
                                    onChange={(e) =>
                                      setEditingExpense({ ...editingExpense, category: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="amount" className="text-right">
                                    Monto
                                  </Label>
                                  <Input
                                    id="amount"
                                    type="number"
                                    value={editingExpense?.amount}
                                    onChange={(e) =>
                                      setEditingExpense({
                                        ...editingExpense,
                                        amount: parseFloat(e.target.value),
                                      })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="date" className="text-right">
                                    Fecha
                                  </Label>
                                  <Input
                                    id="date"
                                    type="date"
                                    value={editingExpense?.date}
                                    onChange={(e) =>
                                      setEditingExpense({ ...editingExpense, date: e.target.value })
                                    }
                                    className="col-span-3"
                                  />
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="approvedBy" className="text-right">
                                    Aprobado por
                                  </Label>
                                  <Select
                                    value={editingExpense?.approvedBy}
                                    onValueChange={(value) =>
                                      setEditingExpense({ ...editingExpense, approvedBy: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      {employees.map((employee) => (
                                        <SelectItem key={employee.id} value={employee.name}>
                                          {employee.name}
                                        </SelectItem>
                                      ))}
                                    </SelectContent>
                                  </Select>
                                </div>
                                <div className="grid grid-cols-4 items-center gap-4">
                                  <Label htmlFor="paymentMethod" className="text-right">
                                    Método de Pago
                                  </Label>
                                  <Select
                                    value={editingExpense?.paymentMethod}
                                    onValueChange={(value) =>
                                      setEditingExpense({ ...editingExpense, paymentMethod: value })
                                    }
                                  >
                                    <SelectTrigger className="col-span-3">
                                      <SelectValue />
                                    </SelectTrigger>
                                    <SelectContent>
                                      <SelectItem value="Efectivo">Efectivo</SelectItem>
                                      <SelectItem value="Tarjeta de crédito">Tarjeta de crédito</SelectItem>
                                      <SelectItem value="Transferencia bancaria">Transferencia bancaria</SelectItem>
                                    </SelectContent>
                                  </Select>
                                </div>
                              </div>
                              <Button onClick={handleUpdateExpense}>Guardar Cambios</Button>
                            </DialogContent>
                          </Dialog>
                          <AlertDialog>
                            <AlertDialogTrigger asChild>
                              <Button
                                variant="destructive"
                                size="sm"
                                className="ml-2"
                              >
                                Eliminar
                              </Button>
                            </AlertDialogTrigger>
                            <AlertDialogContent>
                              <AlertDialogHeader>
                                <AlertDialogTitle>¿Estás seguro?</AlertDialogTitle>
                                <AlertDialogDescription>
                                  Esta acción no se puede deshacer. Esto eliminará permanentemente el gasto.
                                </AlertDialogDescription>
                              </AlertDialogHeader>
                              <AlertDialogFooter>
                                <AlertDialogCancel>Cancelar</AlertDialogCancel>
                                <AlertDialogAction onClick={() => handleDeleteExpense(expense.id)}>
                                  Eliminar
                                </AlertDialogAction>
                              </AlertDialogFooter>
                            </AlertDialogContent>
                          </AlertDialog>
                        </TableCell>
                      </TableRow>
                    ))}
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          )}

          {activeTab === 'reports' && (
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              <Card>
                <CardHeader>
                  <CardTitle>Niveles de Stock</CardTitle>
                </CardHeader>
                <CardContent>
                  <ResponsiveContainer width="100%" height={300}>
                    <BarChart data={stockData}>
                      <CartesianGrid strokeDasharray="3 3" />
                      <XAxis dataKey="name" />
                      <YAxis />
                      <Tooltip />
                      <Legend />
                      <Bar dataKey="actual" fill="#8884d8" name="Stock Actual" />
                      <Bar dataKey="minimo" fill="#82ca9d" name="Stock Mínimo" />
                      <Bar dataKey="maximo" fill="#ffc658" name="Stock Máximo" />
                    </BarChart>
                  </ResponsiveContainer>
                </CardContent>
              </Card>
              <Card>
                <CardHeader>
                  <CardTitle>Ventas Mensuales</CardTitle>
                </CardHeader>
                <CardContent>
                  <ResponsiveContainer width="100%" height={300}>
                    <LineChart data={salesData}>
                      <CartesianGrid strokeDasharray="3 3" />
                      <XAxis dataKey="name" />
                      <YAxis />
                      <Tooltip />
                      <Legend />
                      <Line type="monotone" dataKey="ventas" stroke="#8884d8" />
                    </LineChart>
                  </ResponsiveContainer>
                </CardContent>
              </Card>
              <Card>
                <CardHeader>
                  <CardTitle>Productos Más Vendidos</CardTitle>
                </CardHeader>
                <CardContent>
                  <ResponsiveContainer width="100%" height={300}>
                    <PieChart>
                      <Pie
                        data={topProducts}
                        cx="50%"
                        cy="50%"
                        labelLine={false}
                        outerRadius={80}
                        fill="#8884d8"
                        dataKey="value"
                      >
                        {topProducts.map((entry, index) => (
                          <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                        ))}
                      </Pie>
                      <Tooltip />
                      <Legend />
                    </PieChart>
                  </ResponsiveContainer>
                </CardContent>
              </Card>
              <Card>
                <CardHeader>
                  <CardTitle>KPIs</CardTitle>
                </CardHeader>
                <CardContent>
                  <div className="space-y-4">
                    <div>
                      <div className="flex justify-between mb-1">
                        <span>Ventas Mensuales</span>
                        <span>75%</span>
                      </div>
                      <Progress value={75} />
                    </div>
                    <div>
                      <div className="flex justify-between mb-1">
                        <span>Satisfacción del Cliente</span>
                        <span>90%</span>
                      </div>
                      <Progress value={90} />
                    </div>
                    <div>
                      <div className="flex justify-between mb-1">
                        <span>Eficiencia del Almacén</span>
                        <span>60%</span>
                      </div>
                      <Progress value={60} />
                    </div>
                  </div>
                </CardContent>
              </Card>
            </div>
          )}

          {activeTab === 'settings' && (
            <Card>
              <CardHeader>
                <CardTitle>Configuración del Sistema</CardTitle>
                <CardDescription>Ajusta las preferencias y configuraciones del sistema</CardDescription>
              </CardHeader>
              <CardContent>
                <div className="space-y-4">
                  <div className="flex items-center justify-between">
                    <Label htmlFor="notifications">Notificaciones por email</Label>
                    <Switch id="notifications" />
                  </div>
                  <div className="flex items-center justify-between">
                    <Label htmlFor="darkMode">Modo oscuro</Label>
                    <Switch id="darkMode" />
                  </div>
                  <div>
                    <Label htmlFor="language">Idioma</Label>
                    <Select defaultValue="es">
                      <SelectTrigger id="language">
                        <SelectValue placeholder="Selecciona un idioma" />
                      </SelectTrigger>
                      <SelectContent>
                        <SelectItem value="es">Español</SelectItem>
                        <SelectItem value="en">English</SelectItem>
                        <SelectItem value="fr">Français</SelectItem>
                      </SelectContent>
                    </Select>
                  </div>
                  <div>
                    <Label htmlFor="currency">Moneda</Label>
                    <Select defaultValue="eur">
                      <SelectTrigger id="currency">
                        <SelectValue placeholder="Selecciona una moneda" />
                      </SelectTrigger>
                      <SelectContent>
                        <SelectItem value="eur">Euro (€)</SelectItem>
                        <SelectItem value="usd">US Dollar ($)</SelectItem>
                        <SelectItem value="gbp">British Pound (£)</SelectItem>
                      </SelectContent>
                    </Select>
                  </div>
                  <div>
                    <Label htmlFor="backupFrequency">Frecuencia de copias de seguridad</Label>
                    <Select defaultValue="daily">
                      <SelectTrigger id="backupFrequency">
                        <SelectValue placeholder="Selecciona la frecuencia" />
                      </SelectTrigger>
                      <SelectContent>
                        <SelectItem value="daily">Diaria</SelectItem>
                        <SelectItem value="weekly">Semanal</SelectItem>
                        <SelectItem value="monthly">Mensual</SelectItem>
                      </SelectContent>
                    </Select>
                  </div>
                  <div>
                    <Label htmlFor="taxRate">Tasa de impuestos (%)</Label>
                    <Input id="taxRate" type="number" defaultValue={21} />
                  </div>
                </div>
              </CardContent>
            </Card>
          )}
        </div>
      </main>
    </div>
  )
}
