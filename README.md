# Administrador-de-gestor-de-usuario
Este código es un gestor de configuraciones de usuario que permite agregar, actualizar, eliminar y visualizar ajustes de preferencias almacenados en un diccionario, garantizando que no haya duplicados y normalizando siempre los datos a minúsculas.

test_settings = {'theme': 'LIGHT', 'notifications': 'enabled', 'volume': 'high'}

def add_setting(dict, tuple):
    key, value = tuple
    key = key.lower()
    value = value.lower()
    if key in dict:
        return f"Setting '{key}' already exists! Cannot add a new setting with this name."
    else:
        dict.setdefault(key, value)
        return f"Setting '{key}' added with value '{value}' successfully!"

def update_setting(dict, tuple):
    key, value = tuple
    key = key.lower()
    value = value.lower()
    if key in dict:
        dict[key] = value
        return f"Setting '{key}' updated to '{value}' successfully!"
    else:
        return f"Setting '{key}' does not exist! Cannot update a non-existing setting."

def delete_setting(dict, key):
    key = key.lower()
    if key in dict:
        del dict[key]
        return f"Setting '{key}' deleted successfully!"
    else:
        return "Setting not found!"

def view_settings(dict):
    if not dict:
        return "No settings available."
    else:
        result = "Current User Settings:\n"
        for key, value in dict.items():
            result += f"{key.capitalize()}: {value}\n"
        return result

print(add_setting({'theme': 'light'}, ('THEME', 'dark')))
print(add_setting({'theme': 'light'}, ('volume', 'high')))

print('---------')

print(update_setting({'theme': 'light'}, ('theme', 'dark')))
print(update_setting({'theme': 'light'}, ('volume', 'high')))

print('---------')

print(delete_setting({'theme': 'light'}, 'theme'))
print(delete_setting({'theme': 'light'}, ''))

print('---------')

print(view_settings({'theme': 'dark', 'notifications': 'enabled', 'volume': 'high'}))
