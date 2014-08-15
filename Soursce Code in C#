using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
//Added Namespaces
using System.IO;

namespace Adobe.CS6.Master.Crack
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            string servers = @"127.0.0.1 192.150.14.69
127.0.0.1 192.150.18.101
127.0.0.1 192.150.18.108
127.0.0.1 192.150.22.40
127.0.0.1 192.150.8.100
127.0.0.1 192.150.8.118
127.0.0.1 209-34-83-73.ood.opsource.net
127.0.0.1 3dns-1.adobe.com
127.0.0.1 3dns-2.adobe.com
127.0.0.1 3dns-2.adobe.com
127.0.0.1 3dns-3.adobe.com
127.0.0.1 3dns-3.adobe.com
127.0.0.1 3dns-4.adobe.com
127.0.0.1 3dns.adobe.com
127.0.0.1 activate-sea.adobe.com
127.0.0.1 activate-sea.adobe.com
127.0.0.1 activate-sjc0.adobe.com
127.0.0.1 activate-sjc0.adobe.com
127.0.0.1 activate.adobe.com
127.0.0.1 activate.adobe.com
127.0.0.1 activate.wip.adobe.com
127.0.0.1 activate.wip1.adobe.com
127.0.0.1 activate.wip2.adobe.com
127.0.0.1 activate.wip3.adobe.com
127.0.0.1 activate.wip3.adobe.com
127.0.0.1 activate.wip4.adobe.com
127.0.0.1 adobe-dns-1.adobe.com
127.0.0.1 adobe-dns-2.adobe.com
127.0.0.1 adobe-dns-2.adobe.com
127.0.0.1 adobe-dns-3.adobe.com
127.0.0.1 adobe-dns-3.adobe.com
127.0.0.1 adobe-dns-4.adobe.com
127.0.0.1 adobe-dns.adobe.com
127.0.0.1 adobe-dns.adobe.com
127.0.0.1 adobe.activate.com
127.0.0.1 adobeereg.com
127.0.0.1 crl.verisign.net
127.0.0.1 CRL.VERISIGN.NET.*
127.0.0.1 ereg.adobe.com
127.0.0.1 ereg.adobe.com
127.0.0.1 ereg.wip.adobe.com
127.0.0.1 ereg.wip1.adobe.com
127.0.0.1 ereg.wip2.adobe.com
127.0.0.1 ereg.wip3.adobe.com
127.0.0.1 ereg.wip3.adobe.com
127.0.0.1 ereg.wip4.adobe.com
127.0.0.1 hl2rcv.adobe.com
127.0.0.1 ood.opsource.net
127.0.0.1 practivate.adobe
127.0.0.1 practivate.adobe.*
127.0.0.1 practivate.adobe.com
127.0.0.1 practivate.adobe.com
127.0.0.1 practivate.adobe.ipp
127.0.0.1 practivate.adobe.newoa
127.0.0.1 practivate.adobe.ntp
127.0.0.1 tss-geotrust-crl.thawte.com
127.0.0.1 wip.adobe.com
127.0.0.1 wip1.adobe.com
127.0.0.1 wip2.adobe.com
127.0.0.1 wip3.adobe.com
127.0.0.1 wip3.adobe.com
127.0.0.1 wip4.adobe.com
127.0.0.1 wwis-dubc1-vip60.adobe.com
127.0.0.1 wwis-dubc1-vip60.adobe.com
127.0.0.1 wwis-dubc1-vip60.adobe.com";

            string strHosts = Environment.GetEnvironmentVariable("WINDIR") + @"\system32\drivers\etc\hosts";
            if (File.Exists(strHosts))
            {
                //READ FILE
                string content;
                content = openFile(strHosts);
                //CHECK IF PATCHED
                int patch = content.IndexOf(servers);
                //SAVE FILE
                if (patch == -1)
                {
                    try
                    {
                        File.Delete(strHosts);
                        content = content + servers;
                        saveFile(strHosts, content);
                        MessageBox.Show("Patched succesfully");
                    }
                    catch (UnauthorizedAccessException)
                    {
                        MessageBox.Show("Run as administrator");
                    }
                }
                else
                {
                    MessageBox.Show("Already patched");
                }
            }
        }


        private void button1_Click(object sender, EventArgs e)
        {
            string x86 = "";
            string x64 = "";

            //check if x86
            if (string.IsNullOrEmpty(Environment.GetEnvironmentVariable("PROGRAMFILES(X86)")))
            {
                x86 = @"C:\Program Files\Adobe\";
            }
            else
            {
                x86 = @"C:\Program Files (x86)\Adobe\";
                x64 = @"C:\Program Files\Adobe\";
            }

            //32-bit amtlib Patch
            if (Directory.Exists(x86) == true)
            {
                string[] files = Directory.GetFiles(x86, "amtlib.dll", SearchOption.AllDirectories);
                foreach (string file in files)
                {
                    if (File.Exists(file))
                    {
                        try
                        {
                            File.Delete(file);
                            File.Copy(@"x86\amtlib.dll", file);
                        }
                        catch (UnauthorizedAccessException)
                        {
                            MessageBox.Show("Run as administrator");
                            return;
                        }
                    }
                }
            }

            //64-bit amtlib Patch
            if (Directory.Exists(x64) == true)
            {
                string[] files = Directory.GetFiles(x64, "amtlib.dll", SearchOption.AllDirectories);
                foreach (string file in files)
                {
                    if (File.Exists(file))
                    {
                        try
                        {
                            File.Delete(file);
                            File.Copy(@"x64\amtlib.dll", file);
                        }
                        catch (UnauthorizedAccessException)
                        {
                            MessageBox.Show("Run as administrator");
                            return;
                        }
                    }
                }
            }
            MessageBox.Show("Patching Done");
        }

        public static string openFile(string filePath)
        {
            StreamReader file = new StreamReader(filePath);
            string content = file.ReadToEnd();
            file.Close();
            return content;
        }

        public static void saveFile(string filePath, string content)
        {
            StreamWriter file = new StreamWriter(filePath);
            file.Write(content);
            file.Close();
        }
    }
}
