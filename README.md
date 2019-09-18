# test


Made some more changes to this file. THis is not a tset.

AAPL = 'https://finance.yahoo.com/quote/AAPL'

def getAAPL(AAPL):
    resAAPLobj = requests.get(AAPL, headers={ "User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.110 Safari/537.36"})
    resAAPLobj.raise_for_status()

    soupAAPL = bs4.BeautifulSoup(resAAPLobj.content, 'lxml')
    elemsAAPL = soupAAPL.select('''#quote-header-info > div.My\(6px\).Pos\(r\).smartphone_Mt\(6px\) >
div.D\(ib\).Va\(m\).Maw\(65\%\).Maw\(60\%\)--tab768.Ov\(h\) > div >
span.Trsdu\(0\.3s\).Fw\(b\).Fz\(36px\).Mb\(-4px\).D\(ib\)''')
    return elemsAAPL[0].text.strip()

priceAAPL = getAAPL('https://finance.yahoo.com/quote/AAPL')
print('AAPL = ' + priceAAPL)
