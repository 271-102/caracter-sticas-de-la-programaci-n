# caracter-sticas-de-la-programaci-n
casandra muyolema 
# hotel_reservas.py

# Clase que representa una habitación del hotel
class Habitacion:
    def __init__(self, numero, tipo, precio):
        self.numero = numero
        self.tipo = tipo
        self.precio = precio
        self.esta_disponible = True

    def reservar(self):
        if self.esta_disponible:
            self.esta_disponible = False
            print(f"Habitación {self.numero} reservada con éxito.")
        else:
            print(f"Habitación {self.numero} no está disponible.")

    def liberar(self):
        self.esta_disponible = True
        print(f"Habitación {self.numero} ahora está disponible.")

# Clase que representa al cliente
class Cliente:
    def __init__(self, nombre, documento):
        self.nombre = nombre
        self.documento = documento

# Clase que gestiona las reservas
class SistemaReservas:
    def __init__(self):
        self.habitaciones = []
        self.reservas = {}

    def agregar_habitacion(self, habitacion):
        self.habitaciones.append(habitacion)

    def mostrar_habitaciones_disponibles(self):
        print("Habitaciones disponibles:")
        for hab in self.habitaciones:
            if hab.esta_disponible:
                print(f"- Habitación {hab.numero} ({hab.tipo}) - ${hab.precio}")

    def hacer_reserva(self, cliente, numero_habitacion):
        for hab in self.habitaciones:
            if hab.numero == numero_habitacion and hab.esta_disponible:
                hab.reservar()
                self.reservas[cliente.nombre] = hab.numero
                return
        print("No se pudo realizar la reserva. Verifique disponibilidad.")

# --- Ejemplo de uso del sistema ---

# Crear el sistema de reservas
sistema = SistemaReservas()

# Agregar habitaciones al sistema
sistema.agregar_habitacion(Habitacion(101, "Simple", 50))
sistema.agregar_habitacion(Habitacion(102, "Doble", 80))
sistema.agregar_habitacion(Habitacion(103, "Suite", 120))

# Crear un cliente
cliente1 = Cliente("Laura Pérez", "1728394850")

# Mostrar habitaciones disponibles
sistema.mostrar_habitaciones_disponibles()

# Hacer una reserva
sistema.hacer_reserva(cliente1, 102)

# Mostrar habitaciones disponibles luego de la reserva
sistema.mostrar_habitaciones_disponibles()
