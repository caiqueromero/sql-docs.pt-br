---
title: Migrando do ADO MD para o ADOMD.NET | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e6d0e3acb77657bcac754b9e6b9392dc2971ce9c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="migrating-from-ado-md-to-adomdnet"></a>Migrando do ADO MD para o ADOMD.NET
  A biblioteca do ADOMD.NET é semelhante à biblioteca do ADO MD (ActiveX Data Objects Multidimensional), uma extensão da biblioteca ADO (ActiveX Data Objects) usada no acesso a dados multidimensionais em aplicativos cliente baseados em COM (Component Object Model). O ADO MD oferece acesso fácil a dados multidimensionais de linguagens não gerenciadas, como o C++ e o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. O ADOMD.NET oferece acesso fácil a dados analíticos (multidimensionais e de mineração de dados) de linguagens gerenciadas, como o [!INCLUDE[msCoName](../../includes/msconame-md.md)] C# e o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET. Adicionalmente, o ADOMD.NET oferece um modelo de objeto de metadados avançado.  
  
 A migração de aplicativos cliente existentes do ADO MD para o ADOMD.NET é fácil, mas existem várias diferenças importantes em relação à ela:  
  
 **Para fornecer acesso a dados e conectividade para os aplicativos cliente**  
 |ADO MD|ADOMD.NET|  
|------------|---------------|  
|Exige referências a Adodb.dll e a Adomd.dll.|Exige uma única referência a Microsoft.AnalysisServices.AdomdClient.dll.|  
  
 A classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> oferece suporte de conectividade, além de acesso a metadados.  
  
 **Para recuperar metadados para objetos multidimensionais**  
 |ADO MD|ADOMD.NET|  
|------------|---------------|  
|Use a classe de catálogo.|Use a propriedade <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A> de <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.|  
  
 **Para executar consultas e retornar objetos de conjunto de células**  
 |ADO MD|ADOMD.NET|  
|------------|---------------|  
|Use a classe de conjunto de células.|Use a classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.|  
  
 **Para acessar os metadados que é usado para exibir um conjunto de células**  
 |ADO MD|ADOMD.NET|  
|------------|---------------|  
|Use a classe de posição.|Use os objetos <xref:Microsoft.AnalysisServices.AdomdClient.Set> e <xref:Microsoft.AnalysisServices.AdomdClient.Tuple>.|  
  
> [!NOTE]  
>  A classe <xref:Microsoft.AnalysisServices.AdomdClient.Position> é suportada para compatibilidade com versões anteriores.  
  
 **Para recuperar metadados de modelo de mineração**  
 No ADO MD não há nenhuma classe disponível. No ADOMD.NET, use uma das coleções de mineração de dados:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> contém uma lista de todos os modelo de mineração da fonte de dados.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> oferece informações sobre os algoritmos de mineração disponíveis.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> exibe informações sobre as estruturas de mineração no servidor.  
  
 Para realçar essas diferenças, o exemplo de migração a seguir compara um aplicativo do ADO MD existente a um aplicativo do ADOMD.NET equivalente.  
  
## <a name="looking-at-a-migration-example"></a>Examinando um exemplo de migração  
 Os exemplos de código do ADO MD e do ADOMD.NET equivalente mostrados nesta seção executam o mesmo conjunto de ações: a criação de uma conexão, a execução de uma instrução MDX (Multidimensional Expressions) e a recuperação de metadados e de dados. No entanto, esses dois conjuntos de código não usam os mesmos objetos na execução dessas tarefas.  
  
### <a name="existing-ado-md-code"></a>Código ADO MD existente  
 O exemplo de código a seguir, retirado da documentação do ADO MD 2.8, escrito em [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic® 6.0 e usa o ADO MD para demonstrar como se conectar e consultar um [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonte de dados. Este exemplo de ADO MD usa os seguintes objetos:  
  
-   Cria uma conexão de um **catálogo** objeto.  
  
-   Executa a instrução MDX (Multidimensional Expressions) usando o **conjunto de células** objeto.  
  
-   Recupera os metadados e dados do **posição** recuperado do objeto de **conjunto de células** objeto.  
  
```  
Private Sub cmdCellSettoDebugWindow_Click()  
Dim cat As New ADOMD.Catalog  
Dim cst As New ADOMD.Cellset  
Dim i As Integer  
Dim j As Integer  
Dim k As Integer  
Dim strServer As String  
Dim strSource As String  
Dim strColumnHeader As String  
Dim strRowText As String  
  
On Error GoTo Error_cmdCellSettoDebugWindow_Click  
Screen.MousePointer = vbHourglass  
'*-----------------------------------------------------------------------  
'* Set server to local host.  
'*-----------------------------------------------------------------------  
    strServer = "LOCALHOST"  
  
'*-----------------------------------------------------------------------  
'* Set MDX query string source.  
'*-----------------------------------------------------------------------  
    strSource = strSource & "SELECT "  
    strSource = strSource & "{[Measures].members} ON COLUMNS,"  
    strSource = strSource & _  
        "NON EMPTY [Store].[Store City].members ON ROWS"  
    strSource = strSource & " FROM Sales"  
  
'*-----------------------------------------------------------------------  
'* Set active connection.  
'*-----------------------------------------------------------------------  
        cat.ActiveConnection = "Data Source=" & strServer & _  
            ";Provider=msolap;"  
  
'*-----------------------------------------------------------------------  
'* Set cellset source to MDX query string.  
'*-----------------------------------------------------------------------  
        cst.Source = strSource  
  
'*-----------------------------------------------------------------------  
'* Set cellset active connection to current connection  
'*-----------------------------------------------------------------------  
    Set cst.ActiveConnection = cat.ActiveConnection  
  
'*-----------------------------------------------------------------------  
'* Open cellset.  
'*-----------------------------------------------------------------------  
    cst.Open  
  
'*-----------------------------------------------------------------------  
'* Allow space for row header text.  
'*-----------------------------------------------------------------------  
strColumnHeader = vbTab & vbTab & vbTab & vbTab & vbTab & vbTab  
  
'*-----------------------------------------------------------------------  
'* Loop through column headers.  
'*-----------------------------------------------------------------------  
       For i = 0 To cst.Axes(0).Positions.Count - 1  
            strColumnHeader = strColumnHeader & _  
                cst.Axes(0).Positions(i).Members(0).Caption & vbTab & _  
                    vbTab & vbTab & vbTab  
       Next  
       Debug.Print vbTab & strColumnHeader & vbCrLf  
  
'*-----------------------------------------------------------------------  
'* Loop through row headers and provide data for each row.  
'*-----------------------------------------------------------------------  
        strRowText = ""  
        For j = 0 To cst.Axes(1).Positions.Count - 1  
            strRowText = strRowText & _  
                cst.Axes(1).Positions(j).Members(0).Caption & vbTab & _  
                    vbTab & vbTab & vbTab  
            For k = 0 To cst.Axes(0).Positions.Count - 1  
                strRowText = strRowText & cst(k, j).FormattedValue & _  
                    vbTab & vbTab & vbTab & vbTab  
            Next  
            Debug.Print strRowText & vbCrLf  
            strRowText = ""  
        Next  
  
    Screen.MousePointer = vbDefault  
Exit Sub  
  
Error_cmdCellSettoDebugWindow_Click:  
   Beep  
   Screen.MousePointer = vbDefault  
   MsgBox "The following error has occurred:" & vbCrLf & _  
      Err.Description, vbCritical, " Error!"  
   Exit Sub  
End Sub  
```  
  
### <a name="equivalent-adomdnet-code"></a>Código ADOMD.NET equivalente  
 O exemplo a seguir, escrito em Visual Basic .NET usando ADOMD.NET, demonstra como executar as mesmas ações do exemplo de Visual Basic 6.0 anterior. A principal diferença entre o exemplo a seguir e o exemplo do ADO MD mostrado anteriormente está nos objetos são usados para a execução das ações. O exemplo de ADOMD.NET usa os seguintes objetos:  
  
-   Cria uma conexão com um **AdomdConnection** objeto.  
  
-   Executa a instrução MDX usando um **AdomdCommand** objeto.  
  
-   Recupera os metadados e dados do **definir** recuperado do objeto de **conjunto de células** objeto.  
  
```  
Private Sub DisplayCellSetInOutputWindow()  
    Dim conn As AdomdConnection  
    Dim cmd As AdomdCommand  
    Dim cst As CellSet  
    Dim i As Integer  
    Dim j As Integer  
    Dim k As Integer  
    Dim strServer As String = "LOCALHOST"  
    Dim strSource As String = "SELECT [Measures].members ON COLUMNS, " & _  
        "NON EMPTY [Store].[Store City].members ON ROWS FROM SALES"  
    Dim strOutput As New System.IO.StringWriter  
  
    '*-----------------------------------------------------------------------  
    '* Open connection.  
    '*-----------------------------------------------------------------------  
    Try  
        ' Create a new AdomdConnection object, providing the connection  
        ' string.  
        conn = New AdomdConnection("Data Source=" & strServer & _  
        ";Provider=msolap;")  
        ' Open the connection.  
        conn.Open()  
    Catch ex As Exception  
        Throw New ApplicationException( _  
            "An error occurred while connecting.")  
    End Try  
  
    Try  
    '*-----------------------------------------------------------------------  
    '* Open cellset.  
    '*-----------------------------------------------------------------------  
        ' Create a new AdomdCommand object, providing the MDX query string.  
        cmd = New AdomdCommand(strSource, conn)  
        ' Run the command and return a CellSet object.  
        cst = cmd.ExecuteCellSet()  
  
    '*-----------------------------------------------------------------------  
    '* Concatenate output.  
    '*-----------------------------------------------------------------------  
  
    ' Include spacing to account for row headers.  
    strOutput.Write(vbTab, 6)  
  
    ' Iterate through the first axis of the CellSet object and  
    ' retrieve column headers.  
    For i = 0 To cst.Axes(0).Set.Tuples.Count - 1  
        strOutput.Write(cst.Axes(0).Set.Tuples(i).Members(0).Caption)  
        strOutput.Write(vbTab, 4)  
    Next  
    strOutput.WriteLine()  
  
    ' Iterate through the second axis of the CellSet object and  
    ' retrieve row headers and cell data.  
    For j = 0 To cst.Axes(1).Set.Tuples.Count - 1  
        ' Append the row header.  
        strOutput.Write(cst.Axes(1).Set.Tuples(j).Members(0).Caption)  
        strOutput.Write(vbTab, 4)  
  
        ' Append the cell data for that row.  
        For k = 0 To cst.Axes(0).Set.Tuples.Count - 1  
            strOutput.Write(cst.Cells(k, j).FormattedValue)  
            strOutput.Write(vbTab, 4)  
        Next  
        strOutput.WriteLine()  
    Next  
  
    ' Display the output.  
    Debug.WriteLine(strOutput.ToString)  
  
    '*-----------------------------------------------------------------------  
    '* Release resources.  
    '*-----------------------------------------------------------------------  
        conn.Close()  
    Catch ex As Exception  
        ' Ignore or handle errors.  
    Finally  
        cst = Nothing  
        cmd = Nothing  
        conn = Nothing  
    End Try  
End Sub  
```  
  
  
