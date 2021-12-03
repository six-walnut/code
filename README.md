func textToImage(drawText text: String, inImage image: UIImage, atPoint point: CGPoint) -> UIImage {
        if text == "" {
            return image
        }
        let drawText = text.substring(toIndex: 1)
       let textColor = UIColor.white
        let textFont = UIFont(name: "PingFangSC-Semibold", size: 20)!
       let scale = UIScreen.main.scale
        UIGraphicsBeginImageContextWithOptions(image.size, false, scale)
       let textFontAttributes = [
        NSAttributedString.Key.font: textFont,
        NSAttributedString.Key.foregroundColor: textColor,
       ] as [NSAttributedString.Key : Any]
       image.draw(in: CGRect(origin: CGPoint.zero, size: image.size))
       let rect = CGRect(origin: point, size: image.size)
       drawText.draw(in: rect, withAttributes: textFontAttributes)
       let newImage = UIGraphicsGetImageFromCurrentImageContext()
       UIGraphicsEndImageContext()
       return newImage!
    }
