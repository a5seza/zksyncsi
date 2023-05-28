# zksyncsi
// 查询原生资产余额，ETH，BNB，MATIC等
  if (["eth", "bnb", "matic"].includes(contractAddress.toLowerCase())) {
    return getEthBalance(walletAddress, network);
  }

  const data = "0x70a08231" + "000000000000000000000000" + walletAddress.slice(2);
  const response = UrlFetchApp.fetch(rpcLink, {
    method: "post",
    payload: JSON.stringify({
      "jsonrpc": "2.0",
      "method": "eth_call",
      "params": [{
        "to": contractAddress,
        "data": data
      }, "latest"],
      "id": 1
