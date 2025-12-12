

CREATE TABLE events (
    event_id SERIAL PRIMARY KEY,
    user_id VARCHAR(50),
    event_type VARCHAR(50), -- 'page_view', 'add_to_cart', 'purchase'
    timestamp TIMESTAMP DEFAULT NOW(),
    channel VARCHAR(50), -- 'organic', 'paid', 'email', 'social'
    revenue DECIMAL(10,2) DEFAULT 0,
    properties JSONB
);

CREATE TABLE sessions (
    session_id VARCHAR(50) PRIMARY KEY,
    user_id VARCHAR(50),
    start_time TIMESTAMP,
    end_time TIMESTAMP,
    pages_viewed INT DEFAULT 0,
    converted BOOLEAN DEFAULT FALSE,
    channel VARCHAR(50)
);

CREATE INDEX idx_events_user ON events(user_id);
CREATE INDEX idx_events_type ON events(event_type);
CREATE INDEX idx_sessions_user ON sessions(user_id);
