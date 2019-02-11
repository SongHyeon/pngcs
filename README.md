# Complete PNG encoding and decoding for Unity engine.

TODO:
- PNG.READ creating Texture2D in every useful TextureFormat (infered from file)
- PNG.READ with target TextureFormat argument
- PNG.READ with target width and height arguemnts
- Improve READ/WRITE speed
- PNG.READ for big files (10k/10k px).
  Color[] is causing problem in these cases since allocating 10k px * 10k px * sizeof(Color) is 1,6GB

HOW TO USE:
```C#
using System.Threading.Tasks;
using UnityEngine;
using using Pngcs.Unity;
public class PngcsTest : MonoBehaviour
{
    [SerializeField] string _inputPath = @"D:/input.png";
    [SerializeField] Texture2D _input;
    [SerializeField] Texture2D _output;
    [SerializeField] string _outputPath = @"D:/output.png";
    async void Awake ()
    {
        if( System.IO.File.Exists( _inputPath ) )
        {
            
            
            // THIS IS HOW YOU READ:
            _input = await PNG.READ( _inputPath );
            
            
            Debug.Log( "PNG.READ successful!" );
        } else { Debug.Log( $"invalid input path, read not tested" , this ); }
        if( _output!=null )
        {
            
            
            // THIS IS HOW YOU WRITE:
            PNG.WRITE( _output , _outputPath );
            
            
            Debug.Log( "PNG.WRITE successful!" );
        } else { Debug.Log( "output field is null, write not tested" , this ); }
    }
}
```
