# octure
flowchart TD
  subgraph Captación
    BD[Base de datos<br/>400 000 registros] -->|60% con consentimiento explícito| Consent[Consentimientos<br/>(explícito/tácito)]
    Mall[Stands en el Mall] --> Leads[Leads (formularios)]
  end

  subgraph Ingesta
    Consent --> CRM[CRM Marketing]
    Leads --> CRM
  end

  subgraph Sincronización
    CRM --> App[App OCTURE]
    App -->|Tickets, transacciones| CRM
  end

  subgraph Segmentación_y_Nurturing
    CRM --> Segment1[Impactados sin instalación]
    CRM --> Segment2[Registrados sin pago móvil]
    CRM --> Segment3[Pago móvil activo]
  end

  subgraph Comunicación_Multicanal
    Segment1 --> Email1[Email<br/>(recordatorio)]
    Segment2 --> Push2[Push app]
    Segment3 --> Push3[Ofertas y recargas]
  end

  subgraph Almacenamiento_y_Protección
    CRM --> SecuredDB[BBDD cifrada (AES-256)]
    SecuredDB --> AuditLog[Registro de acceso y cambios]
  end

  subgraph Eliminación_y_Retención
    SecuredDB --> RetPolicy[Política de retención<br/>6 meses – 2 años]
    RetPolicy --> Borrado[Borrado seguro]
  end
