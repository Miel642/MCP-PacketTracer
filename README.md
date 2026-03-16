# MCP-PacketTracer
Este proyecto implementa un servidor basado en el Model Context Protocol (MCP) que actúa como puente entre Claude AI y Cisco Packet Tracer. Permite la creación, configuración y diagnóstico de topologías de red mediante lenguaje natural, transformando a la IA en un asistente de red con capacidades de ejecución directa sobre el simulador.

# Capacidades Principales
- Diseño Automatizado: Generación instantánea de nodos (Routers, Switches, PCs) y cableado.
- Configuración Inteligente: Gestión de direccionamiento IP, protocolos de enrutamiento (OSPF, RIP) y servicios de red sin intervención manual en la CLI.
- Troubleshooting Asistido: Diagnóstico de conectividad y auditoría de configuraciones en tiempo real.
- Interoperabilidad: Uso de transporte stdio para una comunicación eficiente y ligera entre procesos.

# Estructura del Proyecto
- src/packet_tracer_mcp/: Núcleo del servidor MCP.
- V1-MCP-BUILDER.pts: Script de automatización para cargar dentro de Cisco Packet Tracer.
- pyproject.toml: Definición de dependencias y empaquetado del proyecto.
- CLAUDE.md: Guía de desarrollo y reglas de contexto para asistentes de IA.

# Desafíos Técnicos Resueltos
- Gestión de Conflictos de Red (Socket 10048): Se identificó y resolvió el conflicto con el puerto nativo de Packet Tracer (39000), redirigiendo la comunicación del servidor MCP al puerto 39001 para permitir la coexistencia de ambos procesos.
- Depuración de Canal STDIO: Se implementó una política de LOG_LEVEL: ERROR para limpiar el flujo de datos stdio. Esto evita que los mensajes de información (INFO) interfieran con las tramas JSON-RPC que Claude espera recibir.
- Sincronización de Procesos: Uso de PYTHONUNBUFFERED para garantizar que las respuestas de la IA se reflejen de inmediato en la topología de Packet Tracer.

# Requisitos Previos
- Cisco Packet Tracer (con soporte de Scripts/API).
- Claude Desktop App.
- Python 3.10 o superior.






