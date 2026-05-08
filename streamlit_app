import streamlit as st
import pandas as pd
import ccxt

# App Configuration
st.set_page_config(page_title="Nithuva Treder Bot", page_icon="📈")

st.title("🤖 Order Flow Pro Dashboard")
st.markdown("---")

# Sidebar for Status
st.sidebar.header("Bot Controls")
status = st.sidebar.toggle("Bot Active", value=True)
st.sidebar.write(f"Status: {'🟢 Running' if status else '🔴 Idle'}")

# Market Overview Section
st.subheader("📊 Market Overview")
exchange = ccxt.binance()
ticker = st.selectbox("Select Trading Pair", ["BTC/USDT", "ETH/USDT", "SOL/USDT"])

if st.button("Get Live Price"):
    data = exchange.fetch_ticker(ticker)
    col1, col2 = st.columns(2)
    col1.metric("Current Price", f"${data['last']}")
    col2.metric("24h Volume", f"{data['quoteVolume']:.2f}")

# Order Flow Levels (Mock Data for UI)
st.subheader("📍 Order Flow Levels (IB)")
c1, c2, c3 = st.columns(3)
c1.metric("IB High", "71,250")
c2.metric("IB Low", "69,800")
c3.metric("POC", "70,450")

# Recent Trade Signals
st.subheader("🔔 Execution History")
signals = pd.DataFrame({
    'Time': ['21:15', '20:45', '19:30'],
    'Signal': ['BUY', 'ABSORPTION', 'SELL'],
    'Price': [69850, 70200, 71200],
    'Status': ['Executed', 'Monitoring', 'Target Hit']
})
st.dataframe(signals, use_container_width=True)

st.info("Note: Connect your Webhook to receive live signals from TradingView.")
