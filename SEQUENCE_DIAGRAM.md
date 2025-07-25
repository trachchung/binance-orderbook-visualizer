# Binance L3 Order Book Visualizer - Simplified Sequence

```mermaid
sequenceDiagram
    participant User
    participant App
    participant WebSocket
    participant Binance
    participant UI

    User->>App: Start with symbol
    App->>Binance: Fetch symbol precision
    App->>WebSocket: Connect to depth stream
    App->>Binance: Get initial snapshot

    loop Real-time Updates
        Binance->>WebSocket: Depth updates
        WebSocket->>App: Process updates
        App->>App: Update order book state
        App->>UI: Render visualization
        UI-->>User: Display chart
    end

    User->>App: Change symbol/mode
    App->>WebSocket: Reconnect with new symbol
    App->>UI: Update visualization mode
```

## Core Flow:

1. **Startup**: Parse args → Fetch precision → Connect WebSocket → Get snapshot
2. **Runtime**: Receive updates → Process order book → Render chart
3. **User Input**: Change symbol/mode → Reconnect → Update display
