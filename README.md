files[i].account_number;
        const profilePassword = data.profiles[i].password;
        const githubRoute = data.profiles[i].githubRepo;
        // END OF DATA FIELD
        await axios.get(`http://local.adspower.com:50325/api/v1/browser/start?user_id=${profileId}`).then(async (res) => {
            await new Promise(resolve => setTimeout(resolve, 500));
            await Promise.waitForNetworkIdle;
            console.log(res.data);
            if (res.data.code == 0 && res.data.data.ws.puppeteer && res.data.data.ws.puppeteer) {
                try {
                    const browser = await puppeteer.connect(
                        { browserWSEndpoint: res.data.data.ws.puppeteer, defaultViewport: null, args: ['--start-fullscreen', '--no-sandbox'],  });
                        
                    // Function Field

                    // #1 METAMASK LOGIN
